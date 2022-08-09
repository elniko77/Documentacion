#### Crear un docker docker compose para actualizar la ip

Generar el token en My profile/api Tokens, dar permisos de modificación en la zona.

docker-compose.yaml
``` yaml
version: '2'
services:
  cloudflare-ddns:
    image: oznu/cloudflare-ddns:latest
    restart: always
    environment:
      - API_KEY=TUAPI
      - ZONE=nss.net.ar
 #    - SUBDOMAIN=subdomain
      - PROXIED=false
      - CRON=0 * * * *
 ```
