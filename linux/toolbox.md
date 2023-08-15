#### En ubuntu instalar flatpak, podman-toolbox y podman:


#### Crear un contenedor
    
    toolbox create -c ubuntu-toolbox -i docker.io/jmennius/ubuntu-toolbox
    toolbox create -c ubuntu22 --image [docker.io/ubuntu:20.04](http://docker.io/ubuntu:20.04)
    toolbox create -d rhel -r  8.3 myrhel
    toolbox create -c rhel83   - - image [registry.access.redhat.com/ubi8/ubi:8.3](http://registry.access.redhat.com/ubi8/ubi:8.3)
    
#### Se pueden ver con podman 


### Distrobox

#### Install
```bash 
   curl -s https://raw.githubusercontent.com/89luca89/distrobox/main/install | sudo sh
```

#### Uso 
```bash
  distrobox-create --name CONTAINER-NAME --image OS-NAME:VERSION
  distrobox-create --name fedoraonfoss --image fedora:36
  distrobox-enter CONTAINER-NAME
  sudo dnf install foliate.noarch
  # Exponerlo al sistema host
  distrobox-export --app foliate
  distrobox stop CONTAINER-NAME
  distrobox rm CONTAINER-NAME

  # Crear con systemd
  distrobox create -n ubuntu -i ubuntu:22.04 --init --additional-packages "systemd"
  distrobox create -i fedora:38 -n fed38systemd --init --additional-packages "systemd"
```




