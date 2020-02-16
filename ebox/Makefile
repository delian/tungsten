include ../common/Makefile.inc

package:
	@echo "Removing old boxes"
	vagrant box remove $(BOXNAME) --force || echo "The box is already removed"
	@echo "Building base-box named $(BOXNAME)"
	vagrant up
	@echo "Stopping the image"
	vagrant halt
	@echo "fix the permissions..."
	sudo chmod a+r /var/lib/libvirt/images/ebox_base.img || echo "Monitor for permission errors"
	@echo "Building the box"
	vagrant package --output $(BOXNAME).box
	@echo "Adding the box to Vagrant"
	vagrant box add $(BOXNAME) $(BOXNAME).box
	@echo "Cleaning up"
	vagrant destroy --force

destroy:
	vagrant destroy --force
	vagrant box remove $(BOXNAME) --force || echo "Box is already removed"
	rm -rf $(BOXNAME).box

clean:
	vagrant destroy --force
	vagrant box remove $(BOXNAME) --force || echo "Box is already removed"
	rm -rf .vagrant _tmp_package
	rm -rf $(BOXNAME).box
