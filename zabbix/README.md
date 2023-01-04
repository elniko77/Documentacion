#### Monitorear docker con el agente

* Instalar el agente
 $ wget -c https://repo.zabbix.com/zabbix/6.2/ubuntu/pool/main/z/zabbix/zabbix-agent2_6.2.6-1%2Bubuntu22.04_amd64.deb

* Agregar el usuario zabbix al grupo docker
* Agregar config para plugin en /etc/zabbix/zabbix_agent2.conf
   Plugins.Docker.Endpoint=unix:///var/run/docker.sock
   
   
