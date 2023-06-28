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
   
   
```
#### Inteface gráfica
```bash
   snap set lxd ui.enable=true
   snap restart --reload lxd
   lxc config set core.https_address :8443
```
