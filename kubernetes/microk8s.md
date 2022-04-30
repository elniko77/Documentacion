

En mi caso bajo una virtual kvm el addon de metallb no asigna ip, revisar
  microk8s no anda el addon metallb

Instalar metallb de la sig forma:

    kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.9.3/manifests/namespace.yaml
    kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.9.3/manifests/metallb.yaml
    kubectl create secret generic -n metallb-system memberlist --from-literal=secretkey="$(openssl rand -base64 128)"
    kubectl apply -f metallbconfig.yaml
    
    # Metal configuracion
    apiVersion: v1
    kind: ConfigMap
    metadata:
      namespace: metallb-system
      name: config
    data:
      config: |
        address-pools:
        - name: my-ip-space
          protocol: layer2
          addresses:
          - 192.168.31.103-192.168.31.103

Traefik:

    microk8s.enable traefik
    # Escucha el ingress en el puerto 8080
    
Escribir la config para poder usar kubectl:

    cd $HOME
    mkdir .kube
    cd .kube
    microk8s config > config
