FROM ubuntu:v2_java
MAINTAINER DanielS

VOLUME ["/hostVolume:/volume"]

#update the current system
RUN apt-get -y update

#Get, Install and run Jenkins
RUN wget -q -O - https://pkg.jenkins.io/debian/jenkins-ci.org.key | apt-key add - 
#RUN mkdir /etc/apt/source.list.d/jenkins.list
RUN sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
RUN apt-get update
RUN apt-get install -y jenkins
RUN service jenkins start

CMD service jenkins start && tail -F /var/log/jenkins/error.log
