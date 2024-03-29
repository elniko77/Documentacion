#### Instalación de microceph

```bash
  $ sudo snap install microceph --channel=latest/edge
  # Bootstrap the cluster
  $ sudo microceph cluster bootstrap
  # Get status
  $ sudo microceph.ceph status
  # List disks
  $ sudo microceph disk list
```
#### Crear 3 discos virtuales para test

```bash
for l in a b c; do
  loop_file="$(sudo mktemp -p /mnt XXXX.img)"
  sudo truncate -s 1G "${loop_file}"
  loop_dev="$(sudo losetup --show -f "${loop_file}")"
  # the block-devices plug doesn't allow accessing /dev/loopX
  # devices so we make those same devices available under alternate
  # names (/dev/sdiY)
  minor="${loop_dev##/dev/loop}"
  sudo mknod -m 0660 "/dev/sdi${l}" b 7 "${minor}"
  sudo microceph disk add --wipe "/dev/sdi${l}"
done

```

#### Conectar microk8s a microceph

```bash
   $ sudo microk8s enable rook-ceph 
   # To connect MicroK8s with an existing Ceph cluster, you can use the helper command
   # 'microk8s connect-external-ceph'. If you are running MicroCeph on the same node, then
   # you can use the following command:

   $ sudo microk8s connect-external-ceph

   # Alternatively, you can connect MicroK8s with any external Ceph cluster using:

   $ sudo microk8s connect-external-ceph \
        --ceph-conf /path/to/cluster/ceph.conf \
        --keyring /path/to/cluster/ceph.keyring \
        --rbd-pool microk8s-rbd
```
