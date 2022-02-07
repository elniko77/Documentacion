## Minikube


Correrlo en linux con kvm como backend:

    $  minikube config set vm-driver kvm2

Comandos básicos:


    $ minikube addons list
    $ minikube start / stop / delete 


Editar la configuración de metallb:

    $ microk8s kubectl edit ConfigMap/config -n metallb-system
    
Dashboard:

    $ minikube dashboard --url
    

## Instalación en Windows 11

    New-Item -Path 'c:\' -Name 'minikube' -ItemType Directory -Force
    Invoke-WebRequest -OutFile 'c:\minikube\minikube.exe' -Uri '[https://github.com/kubernetes/minikube/releases/latest/download/minikube-windows-amd64.exe](https://github.com/kubernetes/minikube/releases/latest/download/minikube-windows-amd64.exe)' -UseBasicParsing

### En otra pestaña agregar el ejecutable al path:

    $oldPath = [Environment]::GetEnvironmentVariable('Path', [EnvironmentVariableTarget]::Machine)
    if ($oldPath.Split(';') -inotcontains 'C:\minikube'){   `[Environment]::SetEnvironmentVariable('Path', $('{0};C:\\minikube' -f $oldPath), [EnvironmentVariableTarget]::Machine)`}
