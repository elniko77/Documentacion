#### Instalación de terraform 


```bash
    $ curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
    $ sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
    $ sudo apt update && sudo apt install terraform

```

#### Instalación de terraformer

```bash
    curl -LO https://github.com/GoogleCloudPlatform/terraformer/releases/download/0.8.15/terraformer-all-linux-amd64
    chmod +x terraformer-all-linux-amd64
    sudo mv terraformer-all-linux-amd64 /usr/local/bin/terraformer
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
    
    
#### Terraformer

Importar infra:
    
    import aws --regions INSERT_AWS_REGIONS_HERE --resources="*" --profile=production
    


