# DockerProject

# To build the jenkins container move to the jenkins folder
docker build -t ubuntu:v3_jenkins .

# To run
docker run -d -p 8006:8080 ubuntu:v3_jenkins

