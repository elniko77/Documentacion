
#### Compactar un disco wsl2

    # Buscar el disco a compactar
    # Ej: C:\Users\youruser\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu22.04LTS_79rhkp1fndgsc\LocalState\ext4.vhdx
    diskpart
    DISKPART> select vdisk file="C:\Users\youruser\WSL\ext4.vhdx”
    DISKPART> compact vdisk


#### Desinstalar una distro

    wsl --unregister Debian
    (hay que borrar el vhdx de C:\Users\nsosa.UCES\AppData\Local\Packages\XXXXX\LocalState)
    
 
