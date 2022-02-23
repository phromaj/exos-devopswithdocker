Ex 1.1
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                     PORTS     NAMES
8a90146c6466   nginx     "/docker-entrypoint.…"   19 seconds ago   Exited (0) 9 seconds ago             jolly_bouman
83a64a17203d   nginx     "/docker-entrypoint.…"   4 minutes ago    Up 4 minutes               80/tcp    magical_leakey
da2dfd04bba5   nginx     "/docker-entrypoint.…"   8 minutes ago    Exited (0) 6 minutes ago             practical_montalcini

Ex 1.2
❯ docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE

~
❯ docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

Ex 1.3
❯ docker pull devopsdockeruh/simple-web-service:ubuntu
❯ docker exec -it 80 bash
root@800178fc42a7:/usr/src/app# tail -f text.log
Secret message is: 'You can find the source code here: https://github.com/docker-hy'

Ex 1.4
docker run -d -it --name ex14 ubuntu sh -c sh -c 'apt update; apt install -y curl; echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'
helsinki.fi

Ex 1.5

