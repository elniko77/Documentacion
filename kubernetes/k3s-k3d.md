
#### Instalar k3d

```bash
   curl -s https://raw.githubusercontent.com/rancher/k3d/main/install.sh | bash
```

#### Crear cluster

```bash
  $ k3d cluster create
```

#### Borrar cluster

```bash
  $ k3d cluster delete
```

#### Crear cluster multimodo

```bash
k3d cluster create --servers 3 --image rancher/k3s:v1.19.3-k3s2
```
