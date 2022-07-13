#### En ubuntu instalar flatpak, podman-toolbox y podman:


#### Crear un contenedor
    
    toolbox create -c ubuntu-toolbox -i docker.io/jmennius/ubuntu-toolbox
    toolbox create -c ubuntu22 --image [docker.io/ubuntu:20.04](http://docker.io/ubuntu:20.04)
    toolbox create -d rhel -r  8.3 myrhel
    toolbox create -c rhel83   - - image [registry.access.redhat.com/ubi8/ubi:8.3](http://registry.access.redhat.com/ubi8/ubi:8.3)
    
#### Se pueden ver con podman    
