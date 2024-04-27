## Remove .git:
- cd Wiki-Cloud9
- sudo rm -rf .git

## Install Docker on Cloud9
- sudo yum install -y docker
- sudo service docker start
- docker --version

## Install Docker Compose on Cloud9
- sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
- sudo chmod +x /usr/local/bin/docker-compose
- docker-compose --version

## Configure settings
- sudo chmod 755 setup.sh
- ./setup.sh
- sudo chmod 755 get_preview_link.sh
- ./get_preview_link.sh
- sudo chmod 757 docker-compose.yml

## Use swarm mode
- sudo docker swarm init
- sudo docker network create --driver overlay flaskapp
- sudo docker stack deploy -c docker-compose.yml wikistack

## Check status
- sudo docker stack ps wikistack
- sudo docker ps

## To scale up, change "replicas: 1" to "replicas: 2" and run the following command multiple times:
- sudo docker stack deploy -c docker-compose.yml wikistack

## To leave swarm mode:
- sudo docker swarm leave --force

## If there are errors:
- sudo lsof -i :5000
- sudo docker ps
