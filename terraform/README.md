#### Instalación de terraform 


```bash
    $ curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
    $ sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
    $ sudo apt update && sudo apt install terraform

```

#### Permiso denegado con libvirtd


```bash
   editar /etc/libvirt/qemu.conf
   
   security_driver = "none"
   
```
