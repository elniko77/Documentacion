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

#### Debuggeando 

    export TF_LOG=TRACE
    
#### Sacar el trace

    export TF_LOG=ERROR

#### Autenticación en provider proxmox

    export PM_API_TOKEN_ID="terraform@pve!terraform-token"
    export PM_API_TOKEN_SECRET="12345abc-a123-4567-b234-1233456789ab"
