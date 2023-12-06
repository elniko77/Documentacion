#### Instalación de requisitos en ubuntu:
```bash
  $ snap install distrobuilder --classic
  $ sudo apt install -y libguestfs-tools wimtools
  $ sudo apt install genisoimage
  $ sudo distrobuilder repack-windows SW_DVD9_Win_Pro_10_21H2_64BIT_Spanish_Pro_Ent_EDU_N_MLF_X22-83650.ISO w10pro-distrobuilder.iso --windows-version=w11
```
#### Instalación de windows 10:
```bash
  $ lxc init win10 --empty --vm -c security.secureboot=false
  $ lxc config device override win10 root size=***30GiB***
  $ lxc config device add win10 iso disk source=/mnt/disco2/w10pro-distrobuilder.iso boot.priority=10
  $ lxc start win10 --console=vga
  Reconectar:
  $ lxc console win10 --type=vga
  Remove dvd:
  $ lxc config device remove win10 iso
  $ lxc config set win11 limits.cpu=4 limits.memory=8GiB
  Add tpm:
  $ lxc config device add win11 vtpm tpm path=/dev/tpm0
```

```bash
   lxd init
   lxc init images:ubuntu/focal test04
   lxc profile create k8s
   $ lxc profile list
   $ lxc list
   $ lxc exec mymachine bash
   $ lxc [stop|start] mymachine
   
   $ lxc remote set-default local
   $ lxc launch images1:rockylinux/9/amd64 rocky9

   $ lxc launch ubuntu:22.04 ubuntu --vm
   $ lxc launch images:ubuntu/22.04/desktop ubuntu --vm -c limits.cpu=4 -c limits.memory=4GiB --console=vga
 
   # setear la pass
   $ lxc exec ubuntu2204-1 -- /bin/bash
     passwd ubuntu
```

#### Crear cluster

```bash
  lxc launch ubuntu:22.04 ubuntu2204-1 --vm
  lxc launch ubuntu:22.04 ubuntu2204-2 --vm

  lxc exec ubuntu2204-1 -- sudo snap install microk8s --classic
  lxc exec ubuntu2204-2 -- sudo snap install microk8s --classic
  lxc exec ubuntu2204-1 -- sudo microk8s.start
  lxc exec ubuntu2204-1 -- sudo microk8s add-node
  lxc exec ubuntu2204-2 -- sudo `microk8s join 192.168.1.230:25000/92b2db237428470dc4fcfc4ebbd9dc81/2c0cb3284b05`
  sudo systemctl restart snap.lxd.daemon
```

#### Exportar e importar una lxd vm
```bash
  $ lxc export win10
  $ lxc import backup.tar.gz win10-restored
  $ lxc start win10-restored --console=vga
```


#### Inteface gráfica
```bash
   snap set lxd ui.enable=true
   snap restart --reload lxd
   lxc config set core.https_address :8443
```

#### NOTAS ** 

 * lxc/lxd no soporta vms en wsl2 porque no se pueden cargar módulos de kernel.
 * Para que los contenedores den ipv4 en fedora, parar firewalld
   - para que funcione la consola gráfica en fedora, instalar virt-viewer, y ejec xhost +
   - Error disk quota exceeded: lxc config device set <instance> root size.state=40GiB



