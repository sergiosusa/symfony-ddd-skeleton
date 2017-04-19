symfony-ddd-skeleton
====================

An empty Symfony 3 project with a self-contained custom development environment on Docker.


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

Ready to use!
 
PHPStorm Configuration
----------------------

1. Create a Docker Interpreter and Docker Server.

![alt text](https://image.ibb.co/fC95d5/phpstorm_conf_dokcer_interpreter.png)

![alt text](https://image.ibb.co/ifJyy5/phpstorm_conf_docker_server.png)

2. Create a PhpUnit configuration.

![alt text](https://image.ibb.co/meOLBQ/phpstorm_conf_phpunit.png)

