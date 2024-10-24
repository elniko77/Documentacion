#### Instalar nixos en wsl2

```cmd
# Download `nixos-wsl.tar.gz` from the latest release -> https://github.com/nix-community/NixOS-WSL/releases/latest
# Import the tarball into WSL:
wsl --import NixOS $env:USERPROFILE\NixOS\ nixos-wsl.tar.gz --version 2
# You can now run NixOS:
wsl -d NixOS
```

#### Compactar un disco wsl2

    # Buscar el disco a compactar
    # Ej: C:\Users\youruser\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu22.04LTS_79rhkp1fndgsc\LocalState\ext4.vhdx
    diskpart
    DISKPART> select vdisk file="C:\Users\youruser\WSL\ext4.vhdx”
    DISKPART> compact vdisk

#### Otra forma de compactar 

    optimize-vhd -Path .\ext4.vhdx -Mode Full

#### Desinstalar una distro

    wsl --unregister Debian
    (hay que borrar el vhdx de C:\Users\nss\AppData\Local\Packages\XXXXX\LocalState)
    
#### Instalar una nueva distro

    Bajar distro para wsl : 

    [https://cloud-images.ubuntu.com/releases/](https://cloud-images.ubuntu.com/releases/)

    `wsl.exe --import <Distribution Name> <Install Folder> <.TAR.GZ File Path>`

     wsl.exe —import ubuntutest C:\Users\nss\Documents\WSL\test-ubuntu C:\Users\nss\Downloads\ubuntu-22.04-server-cloudimg-amd64-wsl.rootfs.tar.gz

#### Listar las distros instaladas

 ```bash
   Get-ChildItem HKCU:\Software\Microsoft\Windows\CurrentVersion\Lxss\ |
   ForEach-Object {
     (Get-ItemProperty $_.PSPATH) | Select-Object DistributionName,BasePath
   }
 ```

#### Mover una instalación de wsl2 a otro disco:
 ```bash
   wsl --list --verbose
   mkdir d:\backuplinux
   wsl --export Ubuntu-18.04 d:\backuplinux\ubuntu.tar
   wsl --unregister Ubuntu-18.04
   mkdir d:\wsl
   wsl --import Ubuntu-18.04 d:\wsl\ d:\backuplinux\ubuntu.tar
   cd %userprofile%\AppData\Local\Microsoft\WindowsApps            **(this is not needed if in path)**
   ubuntu1804.exe config --default-user yourloginname
 ```

#### Modo bridge network
Modo bridge (solo w11) , poner en .wslconfig ($HOME):
```bash
   [wsl2]
   networkingMode=bridged
   vmSwitch=mi-switch
   ipv6=true
```

