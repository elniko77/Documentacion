### Install Vagrant


* Instalar vagrant

    $ apt install vagrant


* Instalar plugin para libvirt 

    $ vagrant plugin install vagrant-libvirt

* Error "mount.nfs: requested NFS version or transport protocol is not supported"

    Editar /etc/nfs.conf y :
    udp=y
