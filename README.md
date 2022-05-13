Folio Wallet System Architecture
    - Nginx 
    - Kibana
    -Mysql
An AWS Admin account would be required with IAM role that enables users to have all permissions enabled.
After a proper AWS user has been created, login with the Admin account.
Search for elastic beanstalk and set it up using the required parameters after analyzing how wide the first users would be.

- Download Docker and create an account on it. 
   Create a  directory on your computer and name it 'Folio Wallet'
   - inside the Folio Wallet, create three folders naming them 'Kibana','Mysql','NGINX'
   - Launch your terminal
    -CD into the folder Folio WAllet/Kibana
    # Kibana is a sub package under elastic so you need to run elastic first, the following command below helps get started with elastic.
        docker network create elastic
        docker pull docker.elastic.co/elasticsearch/elasticsearch:6.4.2
        docker run --name es-node01 --net elastic -p 9200:9200 -p 9300:9300 -t docker.elastic.co/elasticsearch/elasticsearch:8.2.0.

        # Certificates and keys are generated for the transport and HTTP layers.
        # The Transport Layer Security (TLS) configuration settings are written to elasticsearch.yml.
        # A password is generated for the elastic user (this will be the credential required for login when the set up is completed).
        # An enrollment token is generated for Kibana( you'll also need this for enrollment).

    - Launch another terminal and run the following command
        docker pull docker.elastic.co/kibana/kibana:6.4.2
        docker run --name kib-01 --net elastic -p 5601:5601 docker.elastic.co/kibana/6.4.2

        # Agenerated link will be written if everything was successful hitherto
        # Copy the link and paste in your browser
        # You'll then be faced with a request to input password, the password that was shown to you would be the password that would be entered
        Open docker compose file and add the following syntax
        version: '2'
services:
  kibana:
    image: docker.elastic.co/kibana/kibana:6.4.2
    environment:
      SERVER_NAME: ''
      ELASTICSEARCH_HOSTS: '["","""]'

    
      -Launch another terminal cd go back to the root folder and cd into Folio Wallet/ Mysql
        docker pull mysql
        $ docker run --name mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag

    -Launch another terminal cd go back to the root folder and cd into Folio Wallet/ NGINX
        docker pull nginx
        -create a file DockerFile (Note without and extension)
        - in the file you can write FROM nginx
        COPY static-html-directory /usr/share/nginx/html
        place this file in same folder as your static files
        #In your terminal you type this
        $docker build -t .
        $ docker run --name mynginx -d some-content-nginx

        #set external port and container port here 
        
        $ docker run --name mynginx -d -p 8080:80 nginx

        # We are done creating the containers required now we have to push the containers to aws ec
        on the terminal 
        on each terminal that was used to create each containers 
        put this(note contsiners is supposed to be split within this 3 regions us-east-1, eu-west-2 3)
        aws ecr get-login-password --region region | docker login --username AWS --password-stdin aws_account_id.dkr.ecr.region.amazonaws.com

        

