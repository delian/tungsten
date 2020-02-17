# This is the tungstenbase box generator

It prepares a local Vagrant base box (upgraded Centos/7, upgraded kernel,
pip, ansible, some tools, kubernetes and docker repo, but not having
installed docker and kubernetes (as we may want to install it later)

## How to build

    cd ebox
    make


The above commands will build and add local vagrant box named "tungstenbase" which could be used by other boxes.
As the build process of the other boxes is going to save the efforts done for the common base box, the total build process will be speed-up

If you want to destroy or clean **make destroy** or **make clean**
