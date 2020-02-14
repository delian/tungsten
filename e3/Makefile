
help:
	@echo "Make usage"
	@echo "  make init     - use after git clone to initialize the environment, do vagrant up and clone the git submodules"
	@echo "  make update   - use it to refresh the git submodules"
	@echo "  make up       - equivalent to vagrant up + vagrant halt and up again, to reboot the machine after re-provision, to enforce the new kernel"
	@echo "  make destroy  - destroys the vagrant vm"
	@echo "  make clean    - removes the uncommitted changes (git reset) and destroys the vagrant vm"


init:
	@echo "Init..."
	@make up
	vagrant ssh-config > .ssh_config
	git submodule update --init --recursive

update:
	git submodule update --recursive --remote

up:
	@echo "Vagrant up"
	@vagrant up
	@echo "Restart the vagrant"
	@vagrant halt
	@vagrant up

destroy:
	vagrant destroy --force

clean:
	@make destroy
	@#rm -rf contrail-ansible-deployer .ssh_config *~ contrail
	git reset HEAD
