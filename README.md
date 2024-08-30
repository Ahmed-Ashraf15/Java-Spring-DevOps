# Backend Java-Spring-Boot 

## Overview

This is a Backend application that is containerized using Docker and integrated with Jenkins for Continuous Integration (CI) and Continuous Deployment (CD) on slaves in AWS.

## Prerequisites

- configure EC2 instance as a slave on Jenkins
- using ansible playbook to install JDK and Docker , add docker group as a secondary group for the user
- install JDK compatible version with jenkins on EC2 instance

## Details
1. project has 2 branches dev,main
2. project build using gradle
3. project using Jenkins multibranch pipeline
   - Dev branch running CI stages consist of Five stages 
      <br>
     . First stage used to add execution permission for gradlew script
     <br>
     . Second stage used for linting test
     <br>
     . Third stage used for building main code
     <br>
     . Fourth stage used for unit test
     <br>
     . Last step used for docerizing the application and push artifacts to repo in docker hub
     <br>
   - Main branch running CD stages to deploy the final output from CI
     <br>
     . CD stage used for pulling and running the container
     
## Usage

- pull image from Dockerhub
```
docker pull ahmedashraf15/java-spring-boot:v1
```
- run container from downloaded image
```
docker run ahmedashraf15/java-spring-boot:v1
```
> [!NOTE]
> Version and host port are changeable
<br>

## Expected result

![Screenshot](imgs/Result.png)
