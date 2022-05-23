### Instalar jenkins en k8s con helm

    helm repo add jenkins [https://charts.jenkins.io](https://charts.jenkins.io/)
    helm repo update
    kubectl create ns jenkins
    helm install <name> jenkins/jenkins -n jenkins
    kubectl  — namespace jenkins port-forward svc/local-jenkins 8080:8080
