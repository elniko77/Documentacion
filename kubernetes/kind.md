## Kind


Instalación en linux:

    # Download the latest version of KinD
    $ curl -Lo ./kind https://github.com/kubernetes-sigs/kind/releases/download/v0.7.0/kind-linux-amd64
    # Make the binary executable
    $ chmod +x ./kind
    # Move the binary to your executable path
    $ sudo mv ./kind /usr/local/bin/

### Borrar un cluster

    $ kind delete cluster --name wslkind

### Archivo de config de ejemplo para un cluster de 3 nodos    
    $ cat << EOF > kind-3nodes.yaml
      kind: Cluster
      apiVersion: kind.x-k8s.io/v1alpha4
      nodes:
        - role: control-plane
        - role: worker
        - role: worker
      EOF

### Y después crearlo con :

    $ kind create cluster --name wslkindmultinodes --config ./kind-3nodes.yaml
