
#### Compactar un disco wsl2

    # Buscar el disco a compactar
    # Ej: C:\Users\youruser\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu22.04LTS_79rhkp1fndgsc\LocalState\ext4.vhdx
    diskpart
    DISKPART> select vdisk file="C:\Users\youruser\WSL\ext4.vhdx”
    DISKPART> compact vdisk


#### Desinstalar una distro

    wsl --unregister Debian
    (hay que borrar el vhdx de C:\Users\nss\AppData\Local\Packages\XXXXX\LocalState)
    
#### Instalar una nueva distro

    Bajar distro para wsl : 

    [https://cloud-images.ubuntu.com/releases/](https://cloud-images.ubuntu.com/releases/)

    `wsl.exe --import <Distribution Name> <Install Folder> <.TAR.GZ File Path>`

     wsl.exe —import ubuntutest C:\Users\nss\Documents\WSL\test-ubuntu C:\Users\nss\Downloads\ubuntu-22.04-server-cloudimg-amd64-wsl.rootfs.tar.gz
