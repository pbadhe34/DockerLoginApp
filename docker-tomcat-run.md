Step by step docker with Tomcat 8.0

For Tomcat8 with Java8 version image 

docker run -d d -p 8090:8080 --name tomcat8 tomcat:8.0-jre8

docker cp tomcat-users.xml tomcat8:/usr/local/tomcat/conf/tomcat-users.xml
 
docker cp TestApp.war tomcat8:/usr/local/tomcat/webapps/App.war


docker exec -t -i tomcat8 /bin/bash

->java -version -->1.8.0_151


The userid and password for loginPage are ashok and morYa

********************************

Build the docker image from DockerFile in current dir


docker build -f Dockerfile-login -t login-app . 

Run the tomcat insoide the docker container


docker run -d --name tomcat login-app

docker run -d -p 8080:8080 --name tomcat login-app
 
 docker tag login-app pbadhe34/apps:login

  docker login
  docker push pbadhe34/apps:login


The host ip is 192.168.99.100

curl http://192.168.99.100:8080
 


-------------------------

To deploy a new web app to Tomcat server in the Container.

docker cp TestApp.war tomcat:/usr/local/tomcat/webapps/TestApp.war


docker inspect --format '{{ .NetworkSettings.Networks.IPAddress }}' tomcat

docker exec -t -i tomcat /bin/bash

->cd conf

->cat tomcat-users.xml

 
For attach to tomcat container 

docker attach tomcat

apt-get update
apt-get install vim

cd /usr/local/tomcat/conf
vim tomcat-users.xml


docker cp <container>:/path/to/file.ext .

docker cp file.ext <container>:/path/to/file.ext

To exit the container's terminal without stopping it?

exit and CTR+C both stop the container.

To detach the tty without exiting the shell,
# use the escape sequence Ctrl-p + Ctrl-q
# note: This will continue to exist in a stopped state once exited (see "docker ps -a")

Docker stop all containers
Here are some handy shortcuts.
List all containers (only IDs) docker ps -aq.
Stop all running containers. docker stop $(docker ps -aq)
Remove all containers. docker rm $(docker ps -aq)
Remove all images. docker rmi $(docker images -q)

**************************************************************************
********************************************************************
  
 
