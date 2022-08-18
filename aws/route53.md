### Dns failover

* EL default para el health check es 3 consecutivos, con un intervalo default de 30 segundos. Route 53 volverá automáticamente al endpoint original.
* Route 53 considera un http 3xx como exitoso, no sigue redirect.
* AWS recomienda un ttl de 60 segundos cuando se usa failover.
* Soporta chequeos https, http o tcp.
* Se puede chequear el contenido que devuelve el endpoint, habilitando “Enable String Matching”
* Si se habilita el health check, cloudwatch dispara una alarma y usa SNS para enviar la notificación.


### Transfiriendo dominio
* To get started, log into your account and click on “Domains”. Then, click the “Transfer Domain” button at the top of the screen and complete the transfer process. Please make sure before you start the transfer process, (1) your domain name is unlocked at your current registrar, (2) you have disabled privacy protection on your domain name (if applicable), and (3) that you have obtained the valid Authorization Code, or “authcode”, from your current registrar which you will need to enter as part of the transfer process.
* Crear el dominio en route 53, y agregar todos los ns de amazon en nic.ar

### Probando delegación

     dig +trace dominio.com.ar

### Viendo el estado de propagación

     https://www.whatsmydns.net/
     
### Listar zonas 

     aws configure
     aws route53 list-hosted-zones-by-name

### Creando un subdominio 
* Para crear un subdominio, crear una nueva hosted zone, con el nombre del subdominio, por ejemplo subdom.ejemplo.com, copiar los 4 nameservers que da aws, en la zona del dominio (ej: ejemplo.com) crear un registro de tipo NS con esos 4 nameservers como valor.




