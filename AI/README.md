
#### Correr openwebui en wsl2 con gpu 

```bash
docker run -d -p 3000:8080 --gpus all 
--add-host=host.docker.internal:host-gateway -v 
open-webui:/app/backend/data --name open-webui --restart always [ghcr.io/open-webui/open-webui:cuda](http://ghcr.io/open-webui/open-webui:cuda)
```

#### Correr deepseek en ollama
```bash
ollama run deepseek-r1
```
