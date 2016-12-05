# DockerProject

## Java
#### First build the java base class from inside the java folder
docker build ubuntu:v2_java .

## Jenkins
docker build -t ubuntu:v3_jenkins .

docker run -d -p 8006:8080 ubuntu:v3_jenkins

