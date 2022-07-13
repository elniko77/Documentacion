### Notas sobre ansible


---

#### Crear la estructura básica para un rol

     ansible-galaxy init roles/nginx

#### Correr un modulo o playbook sin usar inventario, para probar cosas puntuales

     ansible all -i 192.168.41.6, -u nss -K -m ping
     ansible all -i 192.168.41.6, -u nss -K -m debug -a "var=hostvars[inventory_hostname]”
