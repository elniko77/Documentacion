#### Instalación

```bash
   kubectl create namespace argocd
   kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
#### Bajar e instalar el binario para la cli

```bash
   wget -c https://github.com/argoproj/argo-cd/releases/download/v2.8.0/argocd-linux-amd64
   sudo mv argocd-linux-amd64 /usr/local/bin/argocd
```

#### Verificar que los pods estén corriendo 

```bash
   kubectl get pods -n argocd
```

#### Obtener la pass en una variable de entorno
```bash
   export argocd_password=$(kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d)
```

#### Forwardear el puerto para poder acceder a la web
```bash
   kubectl port-forward svc/argocd-server -n argocd 8080:443
```

#### Loguearse y acceder por cli
```bash
   argocd login  --insecure --username=admin --password=${argocd_password} localhost:8080
   argocd login  --insecure --username=admin --password=${argocd_password} localhost:8080
```

#### Linea de comandos
```bash
   # Crear una app
   argocd app create miapp --repo https://github.com/christianh814/kbe-apps.git --path 00-deploying-application --dest-namespace default --dest-server https://kubernetes.default.svc --directory-recurse
   # Ver info de una app
   argocd app get miapp
```

