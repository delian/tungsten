
help:
	@echo "Make"


init:
	@echo "Init..."
	@make up
	vagrant ssh-config > .ssh_config
	[ -d contrail-ansible-deployer ] || git clone http://github.com/Juniper/contrail-ansible-deployer

up:
	@echo "Vagrant up"
	@vagrant up

destroy:
	vagrant destroy --force