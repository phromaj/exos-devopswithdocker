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
Dockefile content:
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
