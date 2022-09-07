#### Instalar la tool en ubuntu
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
    unzip awscliv2.zip
    sudo ./aws/install


#### Creando perfiles 

    ~/.aws/credentials
    [default]
    aws_access_key_id=AKIAIOSFODNN7EXAMPLE
    aws_secret_access_key=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY

    [user1]
    aws_access_key_id=AKIAI44QH8DHBEXAMPLE
    aws_secret_access_key=je7MtGbClwBF/2Zp9Utk/h3yCo8nvbEXAMPLEKEY
    
    
    ~/.aws/config
    [default]
    region=us-west-2
    output=json

    [profile user1]
    region=us-east-1
    output=text
    
#### Especificar profile

    $ aws ec2 describe-instances --profile user1
    $ export AWS_PROFILE=user1
