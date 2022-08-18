
#### Instalar helm

    $ curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
    $ chmod 700 get_helm.sh
    $ ./get_helm.sh
    
#### Buscar repositorios 

    $ helm search hub wordpress
    $ helm search hub wordpress  --max-col-width=0   (ver mejor la columna)
    
#### Ver la lista de repos instalados

    $ helm repo list
    

#### Instalación de wp como ejemplo


    $ helm repo add bitnami https://charts.bitnami.com/bitnami
    # Ver versiones disponibles
    $ helm search repo wordpress --versions
    # Ver el readme de una versión específica
    $ helm show readme bitnami/wordpress --version 10.0.3
    # Ver los values del chart
    $ helm show values bitnami/wordpress --version 10.0.3
    
    # Modificando los values 
    * Crear el archivo wordpress-values.yaml
      $ touch wordpress-values.yaml
    
    * Editarlo con las opciones requeridas
       wordpressUsername: admin
       wordpressPassword: admin
       wordpressEmail: tuemail@example.com
       wordpressFirstName: admin1
       wordpressLastName: admin1
       wordpressBlogName: blogexample.com
       service: 
         type: LoadBalancer
 
     # Crear el namespace
     $ kubectl create namespace nswordpress
     
     # Instalar el chart con los valores customizados
     $ helm install wordpress bitnami/wordpress --values=wordpress-values.yaml --namespace nswordpress --version 10.0.3

     # Obtener la url del wp
     $ export NODE_IP=$(kubectl get nodes --namespace nswordpress -o jsonpath="{.items[0].status.addresses[0].address}")
echo "WordPress URL: http://$NODE_IP:$NODE_PORT/"
    
     # Obtener la pass
     $ echo Password: $(kubectl get secret --namespace nswordpress wordpress -o jsonpath="{.data.wordpress-password}" | base64 -d)
         
     # IR chequeando el status de los resources pertenecientes al wp
     $ watch -x kubectl get all --namespace nswordpress
    
    
