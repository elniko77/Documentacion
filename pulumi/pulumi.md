#### Instalación 

```bash
   $ wget -c https://get.pulumi.com/releases/sdk/pulumi-v3.67.0-linux-x64.tar.gz
   $ tar xfvz pulumi-v3.67.0-linux-x64.tar.gz
   $ sudo mv ./pulumi/pulumi /usr/local/bin
   $ sudo mv ./pulumi/pulumi-language-go /usr/local/bin/
   $ sudo mv ./pulumi/pulumi-language-python /usr/local/bin/
```

#### Crear nuevo proyecto (go)

```bash
   $ pulumi login --local
   $ pulumi new go
    --description "Creates a Ubuntu 20.04 VM via libvirt" \
    --name pulumi-libvirt-ubuntu --stack dev
   # Bajar el sdk para libvirt
   $ go get github.com/pulumi/pulumi-libvirt/sdk@v0.2.1

```
