
help:
	@echo "Make"


init:
	@echo "Init..."
	@make up
	vagrant ssh-config > .ssh_config
	@#[ -d contrail-ansible-deployer ] || git clone -b R5.0 http://github.com/Juniper/contrail-ansible-deployer
	git submodule update --init --recursive

update:
	git submodule update --recursive --remote

up:
	@echo "Vagrant up"
	@vagrant up

destroy:
	vagrant destroy --force

clean:
	@make destroy
	@#rm -rf contrail-ansible-deployer .ssh_config *~ contrail
	git reset HEAD
