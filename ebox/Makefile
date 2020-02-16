BOXNAME=ebox

package:
	@echo "Removing old boxes"
	vagrant box remove $(BOXNAME) --force || echo "The box is already removed"
	@echo "Building base-box named $(BOXNAME)"
	vagrant up
	@echo "Stopping the image"
	vagrant halt
	@echo "fix the permissions..."
	 sudo chmod a+r /var/lib/libvirt/images/ebox_controller.img
	@echo "Building the box"
	vagrant package --output $(BOXNAME).box
	@echo "Adding the box to Vagrant"
	vagrant box add --box-version 1 $(BOXNAME) $(BOXNAME).box
	@echo "Cleaning up"
	vagrant destroy --force

destroy:
	vagrant destroy --force
	vagrant box remove $(BOXNAME) --force || echo "Box is already removed"
	rm -rf $(BOXNAME).box

clean:
	vagrant destroy --force
	rm -rf .vagrant _tmp_package
	vagrant box remove $(BOXNAME) --force || echo "Box is already removed"
	rm -rf $(BOXNAME).box
	