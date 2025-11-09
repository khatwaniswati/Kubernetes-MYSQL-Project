# Project Description
This is a simple Docker Project to fetch the product list using GET API, build docker image and push to the docker hub.

# Steps To Run The Project

    1. mvn clean package
    2. docker-compose build
    3. docker-compose up 

# Steps To Push Image To The DockerHub
    Step 1: Create an Account on Docker hub (hub.docker.com)

    Step 2: Run docker login on terminal and provide the username and password
   
    Step 3: Tag the image:
        docker tag <image-name>:<version> <username>/<image-name>
        e.g. docker tag product-service:v0.0.1 swati22rs/product-service 
   
    Step 4: Push the image:
        docker push <username>/<image-name>:<version>
        e.g. docker push swati22rs/product-service:v0.0.1
