BOXNAME=ebox

package:
	@echo "Building base-box named $(BOXNAME)"
	vagrant up
	@echo "Stopping the image"
	vagrant halt
	@echo "Building the box"
	vagrant package --output $(BOXNAME).box
	@echo "Adding the box to Vagrant"
	vagrant box add $(BOXNAME) $(BOXNAME).box
	@echo "Cleaning up"
	vagrant destroy --force

clean:
	rm -rf .vagrant _tmp_package
