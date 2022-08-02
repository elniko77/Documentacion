#### Creando un template

     qm set 900 --serial0 socket --vga serial0
     mv ubuntu-22.04-minimal-cloudimg-amd64.img ubuntu-22.04.qcow2
     qemu-img resize ubuntu-22.04.qcow2 80G
     qm importdisk 900 ubuntu-22.04.qcow2 local-lvm
     
     sudo apt install qemu-guest-agent
     
     
#### Si después del update no se puede loguear

```
systemctl stop pve-cluster corosync
pmxcfs -l
rm /etc/corosync/*
rm /etc/pve/corosync.conf
killall pmxcfs
systemctl start pve-cluster

```


#### Sacar el mensaje al loguearse que dice que no está registrado 

```
sed -i.backup -z "s/res === null || res === undefined || \!res || res\n\t\t\t.data.status.toLowerCase() \!== 'active'/false/g" /usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js && systemctl restart pveproxy.service
```