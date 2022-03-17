docker-compose.yml

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


