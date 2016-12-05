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
