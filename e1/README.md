# Experiment 1

This is an experiment for deployment of Tungsten Fabric (Juniper Contrail) on top of Vagrant.
The current state is incomplete (and doesn't work).

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
