Vagrant V1.9.1 with Oracle Virtualbox V5.1. Debian 8, Jessie-64bit. Basic setup.

Virtualbox setup:
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo
apt-key add -

sudo apt-get install virtualbox 5.1

edit /etc/apt/sources.list: deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian <your distro> Contrib
(V10=Buster, V9=Stretch, V8=Jessie)

Virtualbox configuration:
Adding a desktop environment
In Debian: run tasksel, select desktop, e.g. Xfce.

In vagrantfile: Remove comments for "Enable vb.gui", "true" and "end"

Vagrant reload

Virtualbox configuration:
Setting the memory for the VM
In vagrantfile: Uncomment VM.memory, adjust MB to need

Vagrant reload

Vagrant setup
Create a project folder, cd to it. One folder for each environment is preferrable and tidy. Multimachine setup in one Vagrantfile is possible.

sudo apt-get install vagrant
Select image from vagrantcloud.com, e.g. Debian/Jessie64

vagrant box add Debian/Jessie64 (downloads the image)

vagrant init Debian/Jessie64 (imports image and creates SSH-user for login)

If linux-headers install is necessary, vagrant will suspend the operation 
as necesary.

The init-commands creates the Vagrantfile for this image.

vagrant plugin install vagrant.vbguest (installs shared folders etc.).

vagrant reload


Vagrant operation:
Running the image: vagrant up (if only one image present)

Logging in to the image: vagrant ssh (if only one image present)

Shutting down the VM: vagrant halt (after logging out of the image)

Fix a botched installation: sudo rm -rf ~/.vagrant.d (user data),/opt/
vagrant,/user/bin/vagrant (the binaries). Appears as a clean install for
vagrant.
