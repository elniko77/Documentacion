#### Montar un share nfs en un volumen

    docker volume create --driver local --opt type=nfs --opt o=nfsvers=4,addr=192.168.1.100 --opt device=:/nfsdata/testvolume nfs-volume

#### Mostrar información del espacio usado por docker

    $ docker system df

#### Customizar el formato de salida

    ~/.docker/config.json 
    {
	"psFormat": "table {{.ID}}\\t{{.Names}}\\t{{.RunningFor}} ago\\t{{.Status}}\\t{{.Ports}}"
    }

#### Crear un volumen cifs

    $  docker volume create \
	--driver local \
	--opt type=cifs \
	--opt device=//uxxxxx.your-server.de/backup \
	--opt o=addr=uxxxxx.your-server.de,username=uxxxxxxx,password=*****,file_mode=0777,dir_mode=0777 \
	--name cif-volume

#### Backup volumen
     
     $ docker run -v /dbdata --name dbstore ubuntu /bin/bash
     $ docker run --rm --volumes-from dbstore -v $(pwd):/backup ubuntu tar cvf /backup/backup.tar /dbdata

#### Restore volumen
     
     $ docker run -v /dbdata --name dbstore2 ubuntu /bin/bash
     $ docker run --rm --volumes-from dbstore2 -v $(pwd):/backup ubuntu bash -c "cd /dbdata && tar xvf /backup/backup.tar --strip 1"



#### Montar un volumen en un contenedor

   docker run -d -it \
   --name [container-name] \
   --mount source=[volume-name],target=[mount-point]\
   [image-name]


   docker run -d -it \
   --name debian-test \        
   --mount source=nfs-volume,target=/mnt debian

   docker run -it --rm --name nfs-test -v nfs-volume:/data alpine sh

#### Creando y montando un volumen nfs desde un docker-compose


```yaml

version: "3.2"

services:
  nginx-nfs:
    image: nginx
    ports:
      - 9988:80
    
    volumes:
      - type: volume
        source: nfs-volume2
        target: /usr/share/nginx/html
        volume:
          nocopy: true
volumes:
  nfs-volume2:
    driver_opts:
      type: "nfs"
      o: "addr=192.168.1.100,nolock,soft,rw"
      device: ":/nfsdata/testvolume"
```

#### Error: "could not find an available, non-overlapping IPv4 address pool among the defaults to assign to the network"

Docker por default crea redes que son /16, por eso hay muy pocas disponibles. Agregar en /etc/docker/daemon.json:

```json
{
  "bip": "10.254.1.1/24",
  "default-address-pools":
  [
          {"base":"10.254.0.0/16","size":28}
  ]
}
```

#### Ver logs en tiempo real de todos los contenedores:

    $ watch 'docker ps --format "{{.Names}}" | sort | xargs --verbose --max-args=1 -- docker logs --tail=8 --timestamps'

#### Hadolint
    
    [https://github.com/hadolint/hadolint]

```bash
docker run --rm -i hadolint/hadolint < Dockerfile
# OR
docker run --rm -i ghcr.io/hadolint/hadolint < Dockerfile
```

Usarlo en gitlab-ci.yml
```bash
  lint:hadolint:
  script: docker run --rm -i hadolint/hadolint < Dockerfile
  stage: tests
```


#### Debuggear un contenedor
```bash
   # Instalar cntr: https://github.com/Mic92/cntr
   $ cntr attach containername

```




