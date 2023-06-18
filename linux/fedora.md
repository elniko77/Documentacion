# Que hacer después de instalar fedora?


### Chrome
---

* Instalar los repos

   ```sh
   $ sudo dnf install fedora-workstation-repositories
   ```


* Habiliar el repositorio de chrome
  
   ```sh 
   $ sudo dnf config-manager --set-enabled google-chrome
   $ sudo dnf install google-chrome-stabley`
   ```
  

*  Instalar los repositorios rpmfusion
  
    ```sh
    $ sudo rpm -Uvh http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
    ```
  
*  Energía: instalar tlp y powertop 
  
    ```sh
    sudo dnf install tlp tlp-rdw
    sudo systemctl enable tlp
    sudo systemctl start tlp
  
    # Si es una notebook thinkpad, además:
    dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
    dnf install https://repo.linrunner.de/fedora/tlp/repos/releases/tlp-release.fc$(rpm -E %fedora).noarch.rpm
    dnf install kernel-devel akmod-acpi_call akmod-tp_smapi

    # Para ver las estadísticas:
    sudo tlp-stat -b
    ```
*  Instalación de software
    
    ```sh
    sudo dnf install gnome-tweak-tool vlc remmina mc
    ```

* Extensiones de gnome:

    ```sh
    - battery time
    - Tray Icons: Reloaded
    - Sound Input & Output Device Chooser
    - Wireguard Indicator 
    ```
 
 * Cliente para gdrive y/o onedrive:
 
    https://www.insynchq.com/
    
 * Cliente de correo: en mi caso uso evolution, porque es el único que soporta exchange.
 
    ```sh
    $ sudo dnf install evolution evolution-ews
    ```
 
 * Instalar el grupo de paquetes para virtualización: (kvm, virt-manager, etc)
 
    ```sh
    sudo dnf install @virtualization 
    sudo usermod  --append --groups libvirt $(whoami)
    ```

* Instalar fonts de ms:
  
    ```sh
    sudo dnf install curl cabextract xorg-x11-font-utils fontconfig
    sudo rpm -i https://downloads.sourceforge.net/project/  mscorefonts2/rpms/msttcore-fonts-installer-2.6-1.noarch.rpm
    ```

* Docker:

   ```sh
   - Instalar el repo
      sudo dnf config-manager \
      --add-repo \
      https://download.docker.com/linux/fedora/docker-ce.repo
    
   - Instalar los paquetes
       sudo dnf install docker-ce docker-ce-cli containerd.io

   - Agregar el usuario al grupo docker
       sudo usermod -aG docker $USER
   ```
* Gnome:
   ```sh
     # Show weekday in the clock
     gsettings set org.gnome.desktop.interface clock-show-weekday true
     # Show battery percentage
     gsettings set org.gnome.desktop.interface show-battery-percentage true
   ```
* Kubernetes: 

    - Minikube: Bajar el paquete directamente ya que no está en los repos:

       ```sh
       curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-latest.x86_64.rpm
       sudo rpm -ivh minikube-latest.x86_64.rpm 

       minikube start
       minikube kubectl -- get pods
       alias kubectl="minikube kubectl --"
       ```
    - Una vez levantado, configurar metallb como loadbalancer y especificar el rango de ips:
    
       ```sh
       minikube addons enable metallb
       # Obtener la ip de minikube, que es de la vm de kvm para poder asignar unas ips en ese rango para el loadbalancer:
       minikube ip
    
       # y configurar el rango:
       minikube addons configure metallb
       ```
 
    - Borrar todo:
    
      ```sh
      minikube delete --all --purge
      ```
