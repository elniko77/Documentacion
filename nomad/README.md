
#### Instalación 
    curl -fsSL [https://apt.releases.hashicorp.com/gpg](https://apt.releases.hashicorp.com/gpg) | sudo apt-key add -

    sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"

    sudo apt-get update && sudo apt-get install nomad

#### UI:

     [http://192.168.31.103:4646/ui/jobs](http://192.168.31.103:4646/ui/jobs)

#### Plan and run jobs:

    nomad plan nico-sample-job.nomad

    nomad run nico-sample-job.nomad

    nomad node status

    nomad server members

#### Status del cliente

    nomad node status -short -self
    
