
#### Crear las vms

```bash
  $ multipass launch --name master -m 2G
  $ multipass launch --name worker1 -m 2G
  $ multipass launch --name worker2 -m 2G
```
#### Destruir las vms

```bash
  $ multipass delete master
  $ multipass purge
```
