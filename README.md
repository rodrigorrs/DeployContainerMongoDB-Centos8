# DeployContainerMongoDB-Centos8
Deploy container mongoDB no Centos8 do zero.

1 - Crie uma conta no Docker.io - https://www.docker.com/

2 - Certifique-se que a porta do Firewall do Servidor está liberada.
- firewall-cmd --zone=public --add-port=27017/tcp --permanent

3 - Instale o Docker Engenir
- dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo
- dnf install docker-ce --nobest -y
- systemctl start docker
- systemctl enable docker
- docker --version

4 - Instale o Docker Compose
- dnf install curl -y  (or) yum install curl -y
- sudo curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
- chmod +x /usr/local/bin/docker-compose
- docker-compose --version

5 - Login em Docker.io
- docker login docker.io
(user)
(passwd)

6 - Baixe o MongoDB e Instale
- sudo docker pull mongo
- sudo docker images
- sudo mkdir -p /mongodata
- sudo docker run -it -v /data/db:/mongodata -p 27017:27017 --name mongodb -d mongo
- sudo docker logs mongodb

7 - Acessar MongoDB
- sudo docker exec -it mongodb bash (or) sudo docker exec -it mongodb /bin/bash
- mongo -host localhost -port 27017
