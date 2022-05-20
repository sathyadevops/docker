

Docker-Compose Install
-----------------------------------
https://docs.docker.com/compose/install/

Method-1:
---------------
   #  sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
   # sudo chmod +x /usr/local/bin/docker-compose
   # sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
   # docker-compose -v

Method-2:
---------------
# sudo apt-get update
# sudo apt-get install docker-compose-plugin
# apt-cache madison docker-compose-plugin
# sudo apt-get install docker-compose-plugin=<VERSION_STRING>

 2.5.0~ubuntu-bionic

# sudo apt-get install docker-compose-plugin=2.5.0~ubuntu-bionic
# docker compose version


  207  docker stop $(docker ps -q)        ---> to stop all running containers
  208  docker rm $(docker ps -aq)         ---> to remove all containers
  209  docker rmi $(docker images -q)   ---> to remove all images

Ex-1:
-------
   # mkdir nginx
   # vi docker-compose.yml

version: '3'
services:
  web:
    image: nginx
    ports:
       - "80:80"
  db:
    image: mysql
    ports:
       - "3306:3306"
    environment:
       - MYSQL_ROOT_PASSWORD=abc123
       - MYSQL_USER=sathya
       - MYSQL_PASSWORD=abc123
       - MYSQL_DATABASE=demodb


Ex-2:
   # mkdir wordpress
   # vi docker-compose.yml

version: "3"
services:
  wordpress:
    container_name: my_wordpress
    image: wordpress
    ports:
      - "8080:80"
    links:
      - mysql
    environment:
      WORDPRESS_DB_HOST: mysql
      WORDPRESS_DB_USER: root
      WORDPRESS_DB_PASSWORD: "12345"
      WORDPRESS_DB_NAME: wordpress
  mysql:
    container_name: my_mysql
    image: "mysql:5.7"
    volumes:
      - ./.mysql:/var/lib/mysql
    environment:
      MYSQL_DATABASE: wordpress
      MYSQL_ROOT_PASSWORD: "12345"
