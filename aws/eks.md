#### Crear cluster

    eksctl create cluster --name mycluster --version 1.21 --region us-east-1 --nodegroup-name standard-workers --node-type t2.micro --nodes 3 --nodes-min 1 --nodes-max 4 --managed

#### Borrar cluster

    eksctl delete cluster --name my-cluster --region region-code
    
    
