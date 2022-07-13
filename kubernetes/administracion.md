


### Corriendo y exponiendo servicio en minikube
``` bash
   kubectl run elnombredetunodo --image=sotobotero/udemy-devops:0.0.1 --port=80 80
   kubectl expose pod elnombredetunodo --type "LoadBalancer" --port 8080 --target-port=80
   minikube service elnombredetunodo
```
