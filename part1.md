Ex 1.1
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                     PORTS     NAMES
8a90146c6466   nginx     /docker-entrypoint.…   19 seconds ago   Exited (0) 9 seconds ago             jolly_bouman
83a64a17203d   nginx     /docker-entrypoint.…   4 minutes ago    Up 4 minutes               80/tcp    magical_leakey
da2dfd04bba5   nginx     /docker-entrypoint.…   8 minutes ago    Exited (0) 6 minutes ago             practical_montalcini

Ex 1.2
docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE

~
docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

Ex 1.3
docker pull devopsdockeruh/simple-web-service:ubuntu
docker exec -it 80 bash
root@800178fc42a7:/usr/src/app# tail -f text.log
Secret message is: 'You can find the source code here: https://github.com/docker-hy'

Ex 1.4
// be sure to launch that command on bash, the input doesn't seem to work on powershell or fish
docker run -d -it --name ex14 ubuntu sh -c 'apt update; apt install -y curl; echo Input website:; read website; echo Searching..; sleep 1; curl http://;'
helsinki.fi

Ex 1.5
devopsdockeruh/simple-web-service   ubuntu    4e3362e907d5   11 months ago   83MB
devopsdockeruh/simple-web-service   alpine    fd312adc88e0   11 months ago   15.7MB

Ex 1.6
Go to : https://hub.docker.com/r/devopsdockeruh/pull_exercise
Give me the password: basics
You found the correct password. Secret message is:
This is the secret message

Ex 1.7
Dockerfile content:
FROM devopsdockeruh/simple-web-service:alpine
CMD server
commands:
docker build . -t web-server
docker run web-server

Ex 1.8
FROM ubuntu:20.04
WORKDIR /usr/src/app
COPY script.sh .
RUN chmod +x script.sh
CMD apt update ; apt install -y curl ; ./script.sh

Ex 1.9
// need to create file beforehand or it will try to write into a folder
touch text.log
docker run --rm -v /home/lucas/exercises-devopswithdocker/text.log:/usr/src/app/text.log devopsdockeruh/simple-web-service

Ex 1.10
docker run -p 1111:8080 web-server

Ex 1.11
FROM openjdk:8
EXPOSE 8080
WORKDIR /usr/src/app
COPY . .
RUN chmod +x mvnw
RUN ./mvnw package
CMD [ "java", "-jar", "./target/docker-example-1.1.3.jar" ]

ex 1.12
FROM node:lts-alpine
EXPOSE 5000
COPY . .
RUN npm install
RUN npm run build
RUN npm install -g serve
CMD [ "serve", "-s", "-l", "5000", "build" ]

ex 1.13
FROM golang:1.16.14-alpine3.15
EXPOSE 8080
WORKDIR /usr/src/app
COPY . .
RUN go build
CMD ./server

ex 1.14
backend dockerfile:
FROM golang:1.16.14-alpine3.15
EXPOSE 8080
WORKDIR /usr/src/app
COPY . .
RUN go build
ENV PORT=8080
ENV REQUEST_ORIGIN=http://localhost:5000
CMD ./server
frontend dockerfile:
FROM node:lts-alpine
EXPOSE 5000
COPY . .
RUN npm install
RUN REACT_APP_BACKEND_URL=http://localhost:8080 npm run build
RUN npm install -g serve
CMD [ "serve", "-s", "-l", "5000", "build" ]
commands:
docker run -p 8080:8080 -d backend
docker run -p 5000:5000 -d frontend

ex 1.15:
https://hubdocker.com/repository/docker/phromaj/socialunifier/general

ex 1.16:
http://exercice-docker.herokuapp.com/
