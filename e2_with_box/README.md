# e2 based on tunsgetnbase box

This is Exteriment 2 (e2) which is based on the tunsgstenbase box (ebox
directory), so the Vagrant build process should be faster, as it skips yum
update and several package installations.

Before you do make, you should ensure that the tunstenbase box is pre-installed
in the local repository (vagrant box list). First go to ebox to build it.

However, here we do the filesystem resize and docker + kubernetes install,
in order to enable the experiments to have the freedom to try builds with or
without Vagrant and with different file sizes.
