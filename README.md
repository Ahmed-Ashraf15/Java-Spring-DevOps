# Java-Spring-Boot APP using DevOps Tools 

## Overview

This project shows how to build a project using DevOps Tools (git,ansible,jenkins,docker,docker compose,docker swarm)

## Prerequisites

- Setting up a Github repo with dev branch
- Configure EC2 instance as a Jenkins slave  
- Create ansible playbook to install JDK and Docker
- Create Docker file to build our app 
- Create Docker Compose file
- Perform lint, test, build , dpeloy stages using pipeline
- Deploying with Docker Swarm

## Architecture

![Screenshot](imgs/Arch.png)

## installing dependencies

- Using Ansible Playbook to install JDK and Docker

```
ansible-playbook java_docker.yaml
```

> [!NOTE]
> You have to add your servers IP in inventory file


## Setting Up Pipeline

### CI Stages

- include 3 main stages

1. Linting Stage
2. Unit Testing Stage
3. Dockerizing Stage

### CD Stage

- Deploy that final result to Dev Enviroment in AWS
- After Approving APP Deployed to Prod Enviroment in AWS

## Building and Testing

- Building image from Dockerfile

```
docker build -t java-spring-boot .
```

![Screenshot](imgs/Building.png)

- run container from downloaded image

```
docker run -p 8080:8080 java-spring-boot
```

![Screenshot](imgs/Result.png)


## Deploying 

- Using Docker Swarm to create deployment node 

```
docker swarm init
```
![Screenshot](imgs/Swarm_init.png)


- Create and Deploy a stack to Docker Swarm Node Using Docker Compose File 

```
docker stack deploy -c docker-compose.yml spring-app
```
![Screenshot](imgs/Stack_result.png)

### Ensure Deployment

- Show Stacks in node

```
docker stack ls
```
![Screenshot](imgs/show%20stacks.png)

- Show Running service for specified stack

```
docker stack services spring-app
```
![Screenshot](imgs/stack_service.png)

- Show Running containers upon that service

```
docker stack ps spring-app
```
![Screenshot](imgs/stack_ps.png)