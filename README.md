# DeployContainerMongoDB-Centos8
Deploy container mongoDB no Centos8

Crie uma conta no Docker.io - https://www.docker.com/

Certifique-se que a porta do Firewall do Servidor está liberada.
1 - firewall-cmd --zone=public --add-port=27017/tcp --permanent

Instale o Docker Engenir
1 - dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo
2 - dnf install docker-ce --nobest -y
3 - systemctl start docker
4 - systemctl enable docker
5 - docker --version

Instale o Docker Compose
1 - dnf install curl -y  (or) yum install curl -y
2 - sudo curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
3 - chmod +x /usr/local/bin/docker-compose
4 - docker-compose --version

Login em Docker.io
1 - docker login docker.io
-user
-passwd

Baixe o MongoDB e Instale
2 - sudo docker pull mongo
3 - sudo docker images
4 - sudo mkdir -p /mongodata
5 - sudo docker run -it -v /data/db:/mongodata -p 27017:27017 --name mongodb -d mongo
6 - sudo docker logs mongodb

Acessar MongoDB
1 - sudo docker exec -it mongodb bash (or) sudo docker exec -it mongodb /bin/bash
2 - mongo -host localhost -port 27017
