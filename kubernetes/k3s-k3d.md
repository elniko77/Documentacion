
#### Instalar k3d

```bash
   curl -sSL https://get.k3s.io | INSTALL_K3S_VERSION="${VERSION_K3S}" sh -s - server --cluster-init --tls-san "$(hostname --fqdn)"
   mkdir -p "$HOME"/.kube
   sudo cp /etc/rancher/k3s/k3s.yaml "$HOME"/.kube/config
   sudo chown "$(id -u)":"$(id -g)" "$HOME"/.kube/config
   sed -i -e "s/127.0.0.1/$(hostname --fqdn)/g" "$HOME"/.kube/config
   export KUBECONFIG="$HOME"/.kube/config
   kubectl cluster-info
```

#### Crear cluster

```bash
  $ k3d cluster create
  # Crearlo exponiendo loadbalancer en el puerto 8081 del host
  $ k3d cluster create --api-port 6550 -p "8081:80@loadbalancer" --agents 2
```

#### Instalar ingress nginx
```bash
  $ kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.8.1/deploy/static/provider/cloud/deploy.yaml
```

#### Ingress ejemplo

```bash
   $ kubectl create deployment nginx --image=nginx
   $ kubectl create service clusterip nginx --tcp=80:80
```

```yaml
# apiVersion: networking.k8s.io/v1beta1 # for k3s < v1.19
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: nginx
  annotations:
    ingress.kubernetes.io/ssl-redirect: "false"
spec:
  rules:
  - http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: nginx
            port:
              number: 80
```

#### Borrar cluster

```bash
  $ k3d cluster delete
```

#### Crear cluster multimodo

```bash
k3d cluster create --servers 3 --image rancher/k3s:v1.19.3-k3s2
```
