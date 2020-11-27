### GlusterFS


Agregar las correspondientes ip a /etc/hosts, en mi caso:

    192.168.31.104 ubuntu2
    192.168.41.254 ubuntu1
    192.168.31.105 centos1

Instalar gluster (ubuntu):
    
    sudo add-apt-repository ppa:gluster/glusterfs-7
    sudo apt update    
    sudo apt install glusterfs-server
    sudo systemctl start glusterd.service
    sudo systemctl enable glusterd.service

Instalar el cliente (centos):

    sudo dnf install glusterfs-client

(Centos):

Abrir los puertos en el fw:

    ubuntu1$ sudo ufw allow from 192.168.31.104 to any port 24007
    ubuntu1$ sudo ufw allow from 192.168.31.105 to any port 49152
    ubuntu2$ sudo ufw allow from 192.168.41.254 to any port 24007
    ubuntu2$ sudo ufw allow from 192.168.31.105 to any port 24007
    
Probar la comunicación:

    ubuntu1$ sudo gluster peer probe ubuntu2

Verificar desde el segundo server:

    ubuntu2$ sudo gluster peer status

Crear un volumen:

    sudo gluster volume create volume_name replica number_of_servers domain1.com:/path/to/data/directory domain2.com:/path/to/data/directory force

Ejemplo:

    sudo gluster volume create dockerdata replica 2 ubuntu1:/gluster-docker-storage ubuntu2:/gluster-docker-storage force

Iniciar el volumen:

    sudo gluster volume start dockerdata

Comprobar el estado de los volumenes:

    sudo gluster volume status


En el cliente crear el dir y montarlo:
    
    sudo mkdir /dockervolume
    sudo mount -t glusterfs ubuntu1:dockerdata /dockervolume









