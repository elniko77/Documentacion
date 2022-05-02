## Minikube


Correrlo en linux con kvm como backend:

    $  minikube config set vm-driver kvm2

Comandos básicos:


    $ minikube addons list
    $ minikube start / stop / delete 


Editar la configuración de metallb:

    $ microk8s kubectl edit ConfigMap/config -n metallb-system


Acceder a un service usando minikube con docker en wsl2 w10/11:

    $ minikube service nginx

    $ minikube service nginx -p multinode-demo   (named cluster)

Multinode:

    $ minikube start --nodes 2 -p multinode-demo

Status named cluster

    $ minikube status -p multinode-demo

Dashboard:

    $ minikube dashboard --url
    

Usando LoadBalancer en wsl2:

    Para usar loadbalancer, hay que deshabilitar el addon en minikube, instalar el cloud: 

    $ kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.44.0/deploy/static/provider/cloud/deploy.yaml

    y para poder acceder a la ip, hacer el tunel
    
    $ minikube tunnel  ingress-nginx-controller

    Con eso podríamos acceder al lb como 127.0.0.1 (localhost)


## Instalación en Windows 11

    New-Item -Path 'c:\' -Name 'minikube' -ItemType Directory -Force
    Invoke-WebRequest -OutFile 'c:\minikube\minikube.exe' -Uri '[https://github.com/kubernetes/minikube/releases/latest/download/minikube-windows-amd64.exe](https://github.com/kubernetes/minikube/releases/latest/download/minikube-windows-amd64.exe)' -UseBasicParsing

### En otra pestaña agregar el ejecutable al path:

    $oldPath = [Environment]::GetEnvironmentVariable('Path', [EnvironmentVariableTarget]::Machine)
    if ($oldPath.Split(';') -inotcontains 'C:\minikube'){   `[Environment]::SetEnvironmentVariable('Path', $('{0};C:\\minikube' -f $oldPath), [EnvironmentVariableTarget]::Machine)`}


## Ingress en minikube con docker bajo wsl2

    minikube addons enable ingress 
    minikube tunnel ( publica el ingress controller en 127.0.0.1)
    * Se puede acceder desde el host

## Configurar el ingress como LoadBalancer (previa correcta config de metallb)

    ```
    apiVersion: v1
    kind: Service
    metadata:
      name: ingress
      namespace: ingress
    spec:
      selector:
        name: nginx-ingress-microk8s
      type: LoadBalancer
      # loadBalancerIP is optional. MetalLB will automatically allocate an IP from its pool if not
      # specified. You can also specify one manually.
      # loadBalancerIP: x.y.z.a
     ports:
       - name: http
         protocol: TCP
         port: 80
         targetPort: 80
       - name: https
         protocol: TCP
         port: 443
        targetPort: 443
    ``` 