### Install Vagrant


* Instalar vagrant

    $ apt install vagrant


* Instalar plugin para libvirt 

    $ vagrant plugin install vagrant-libvirt
    
* Instalar plugin para las vbox guest tools

    $ vagrant plugin install vagrant-vbguest

* Error "mount.nfs: requested NFS version or transport protocol is not supported"

    Editar /etc/nfs.conf y :
    udp=y
