# e2 based on tunsgetnbase box

This is Exteriment 2 (e2) which is based on the tunsgstenbase box (ebox
directory), so the Vagrant build process should be faster, as it skips yum
update and several package installations.

Before you do make, you should ensure that the tunstenbase box is pre-installed
in the local repository (vagrant box list). First go to ebox to build it.

However, here we do the filesystem resize and docker + kubernetes install,
in order to enable the experiments to have the freedom to try builds with or
without Vagrant and with different file sizes.

---

This is an experiment for deployment of Tungsten Fabric (Juniper Contrail) on top of Vagrant.
Vagrant prepares the virtual machines for the ansible execution.

Experiment 2 builds 3 virtual machines connected to the same network, using in total 16GB of ram:
* Controller (12GB RAM)
* Gateway (2GB RAM)
* Remote (2GB RAM)

The controller has the full instances of Tungsten fabric, while the Gateway
and Remote just have the vrouter and the vrouter-agent.
In addition there is a Kubernetes installed, where the master is on the
Controller and the Gateway and Remote are Kubelet nodes.
The ansible script installs Tungsten Fabric as CNI.

## Warning
It is still not clear to us do we need to have Flannel in addition to Tungsten to enable IP address provisioning.

## How to use make?

The deployment automation is helped by Makefile.

The following commands exist:

Once you clone the repository, you should do

    make init

**make init** will build the Vagrant image (vagrant up), will run git submodules (clone Juniper contrail ansible deployer)
and export vagrant ssh-config into the .ssh_config file

    make update

**make update** updates the submodules recursivelly

    make up

**make up** executes vagrant up, provisions the machine and then restarts it (halt + up) in order to ensure that the new kernel is in use

    make destroy

**make destroy** destroys the vagrant vm

    make clean

**make clean** destroys the vagrant vm and also removes all your uncommitted changed (basically git reset HEAD)


## How to install Tungsten Fabric after the vagrant machines are up

Execute the following commands carefully (as user vagrant on the Controller):

    vagrant ssh controller
    cd contrail-ansible-deployer
    ansible-playbook -e orchestrator=kubernetes -i inventory/ playbooks/configure_instances.yml
    ansible-playbook -e orchestrator=kubernetes -i inventory/ playbooks/install_k8s.yml
    ansible-playbook -e orchestrator=kubernetes -i inventory/ playbooks/install_contrail.yml


After the successful completion, check the status with:

    sudo contrail-status

