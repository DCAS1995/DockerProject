# DockerProject

## Jenkins
docker build -t ubuntu:v3_jenkins .

docker run -d -p 8006:8080 ubuntu:v3_jenkins

