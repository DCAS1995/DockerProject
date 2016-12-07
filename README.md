# DockerProject

## Java
### First build the java base class from inside the java folder
#### This needs to be done this way as all that depend on java will build on this model
docker build ubuntu:v2_java .

## Execute the commands from within the corresponding folders

## Jenkins
docker build -t ubuntu:v3_jenkins .

docker run -d -p 8006:8080 ubuntu:v3_jenkins


## Jira
docker build -t ubuntu:v4_jira .

docker run -d -p 8007:8081 ubuntu:v4_jira

## Nexus
docker build -t ubuntu:v5_nexus .

docker run -d -p 8008:8081 ubuntu:v5_nexus

## Zabbix
docker build -t ubuntu:v6_zabbix .

docker run -dit -p 80:80 ubuntu:v6_zabbix

Go to localhost/zabbix

### Pre installation

DBhost=localhost

DBPort=3306

DBname=zabbixdb

DBUser=zabbix

DBpassword=123

### Post Install Login 

User=Admin

Password=zabbix


## Tomcat
docker build -t ubuntu:v7_tomcat .

docker run -dit -p 8010:8080 ubuntu:v7_tomcat

## Postfix
docker build -t ubuntu:v8_postfix .

docker run -it ubuntu:v8_postfix bash
postfix start
