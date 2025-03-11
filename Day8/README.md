🔹 Challenge 1: Write a simple Dockerfile that runs a Python script using an official base image (python:3.9) or serves a static HTML page using Nginx.

python/Dockerfile:


FROM python:3.9

WORKDIR /app

COPY python/hello.py .

CMD ["python", "hello.py"]


nginx/Dockerfile:


FROM nginx

COPY nginx/index.html /usr/share/nginx/html/index.html

EXPOSE 80


🔹 Challenge 2: Build a Docker image from your Dockerfile and tag it with a version (docker build -t myapp:v1 .).


Building Image from Dockerfile with tag:

#PYTHON SCRIPT 

docker build -t python_script:v1 -f python/Dockerfile .

#NGINX APP

docker build -t nginx_app:v1 -f nginx/Dockerfile .

Verify image with tags:

docker images


🔹 Challenge 3: Run a container from your custom image, map necessary ports, and test the app.

Running Containers:

#python_script container, should display "Hello Prity" wih docker logs

docker run -d --name python_script python_script:v1

docker logs <container_id_python_script>

#nginx container

docker run -d -p 8080:80 --name nginx_app nginx_app:v1

curl http://localhost:8080  #should display below content


<!DOCTYPE html>
<html lang="en">
        <head>
                    <meta charset="UTF-8">
                        <meta name="viewport" content="width=device-width, inile=1.0">
                            <title>Welcome</title>
        </head>
        <b  <h1>Hello from Nginx running in Docker!</h1>
                </body>
</html>



🔹 Challenge 4: Push your custom Docker image to Docker Hub.

docker login

docker tag nginx_app:v1 prityks/nginx_app:v1

docker push prityks/nginx_app:v1



🔹 Challenge 5: Use docker exec -it <container_id> bash to enter a running container and explore it.

docker exec -it <container_id> /bin/bash


🔹 Challenge 6: Run a detached container (-d flag), restart it, and check logs (docker logs <container_id>).

docker run -d -p 8080:80 --name nginx_app nginx_app:v1

docker restart <container_id>

docker logs <container_id>




