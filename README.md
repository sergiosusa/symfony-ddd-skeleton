symfony-ddd-skeleton
====================

An empty Symfony 3 project with a self-contained custom development environment on Docker.

Include: 

- Nginx + php7-fpm
- MySql

Prerequisites
-----

- [Docker](https://docs.docker.com/engine/installation/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

Usage
-----

1. Clone the Project.
2. Copy /provision/development/docker-compose.yml.dist to project root removing .dist extension.
3. Start containers using: 
```
docker-compose up -d --build
```

Access via web:  
http://symfony-ddd-skeleton.dev/ (PROD)  
http://symfony-ddd-skeleton.dev/app_dev.php (DEV)

Access to php-fpm:
```
docker exec -it app_dev_fpm  bash
```

Ready to use! 
 
PHPStorm Configuration
----------------------

1. Create a Docker Interpreter and Docker Server.

![alt text](https://image.ibb.co/fC95d5/phpstorm_conf_dokcer_interpreter.png)

![alt text](https://image.ibb.co/ifJyy5/phpstorm_conf_docker_server.png)

Check out if your Docker container is correctly configured (specially the host path): 

![alt text](https://image.ibb.co/kK10wQ/phpstorm_docker_container_settings.png)

2. Create a PhpUnit configuration.

![alt text](https://image.ibb.co/meOLBQ/phpstorm_conf_phpunit.png)

