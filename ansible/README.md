### Notas sobre ansible


---

#### Crear la estructura básica para un rol

     ansible-galaxy init roles/nginx

#### Correr un modulo o playbook sin usar inventario, para probar cosas puntuales

     ansible all -i 192.168.41.6, -u nss -K -m ping
     ansible all -i 192.168.41.6, -u nss -K -m debug -a "var=hostvars[inventory_hostname]”
 
     # Run the playbook (dry-run)
     $ ansible-playbook -i IP_ADDRESS, --check --diff playbook.yml
     # Run the playbook (for real)
     $ ansible-playbook -i IP_ADDRESS, playbook.yml

#### Variables
Las variables se pueden incluir inline, con vars: o incluir un archivo con vars_files: . 
Se referencian como "{{ variable name }}"

```yaml
   vars:
       key_file:  /etc/apache2/ssl/mywebsite.key
       cert_file: /etc/apache2/ssl/mywebsite.cert
       server_name: www.mywebsite.com
   vars_files:
        - apacheconf.yml
   # Uso     
   - name: 
      uri:
        url: http://{{variable_name}}/index.php
        status_code: 200      
   

```

#### Conexión por primera vez, preguntar pass, usar solo 1 host
      
      ansible all  -i 192.168.31.109, -u nss -m ping --ask-pass
      ansible-playbook -i 192.168.31.109, -u nss --ask-pass main.yaml
      
#### Especificar un inventory distinto y un grupo de servers

      ansible-playbook -i /home/nss/ansible-test-inventory -l ubuntu-vm -u nss -K  --ask-pass install-server-packages/install-packages.yml
      
