#### Montar un share nfs en un volumen

    docker volume create --driver local --opt type=nfs --opt o=nfsvers=4,addr=192.168.1.100 --opt device=:/nfsdata/testvolume nfs-volume

#### Montar un volumen en un contenedor

   docker run -d -it \
   --name [container-name] \
   --mount source=[volume-name],target=[mount-point]\
   [image-name]


   docker run -d -it \
   --name debian-test \        
   --mount source=nfs-volume,target=/mnt debian

   docker run -it --rm --name nfs-test -v nfs-volume:/data alpine sh

