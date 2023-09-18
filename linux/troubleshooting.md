#### Mostrar i/o de procesos de forma acumulativa
```bash
  $ sudo iotop -oPab
```
#### Ver procesos escribiendo al archivo php7.2-fpm.log
```bash
  $ sudo lsof /var/log/php7.2-fpm.log
```
#### Ver que app tiene abierto el puerto 8080
```bash
  $ sudo ss -l -n -p | grep 8080
```

#### Journalctl
```bash
  # Logs desde 2 horas atrás
  $ sudo journalctl -r --since "2 hours ago"
  # Logs del servicio ssh
  $ sudo journalctl -r -u ssh
```

#### Busquedas
```bash
  # Buscar errorcode 500 en la 9na columna
  $ sudo awk '($9 ~ /500/)' /var/log/nginx/access.log
  # Error 404 SOLO en POST
  $ sudo awk '($9 ~ /404/) {if (/POST/) print}' /var/log/nginx/access.log
```
