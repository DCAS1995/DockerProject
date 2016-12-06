FROM ubuntu:v2_java
MAINTAINER DanielS <dcas1995@gmail.com>

RUN apt-get update

#Download and install tomcat
WORKDIR /opt
RUN wget http://mirrors.ukfast.co.uk/sites/ftp.apache.org/tomcat/tomcat-7/v7.0.73/bin/apache-tomcat-7.0.73.tar.gz
RUN tar zxvf apache-tomcat-7.0.73.tar.gz

#Update the .bashrc file
WORKDIR ~
RUN echo 'export JAVA_HOME=/opt/jdk1.8.0_05' > .bashrc
RUN echo 'export CATALINA_HOME=/opt/apache-tomcat-7.0.73' > .bashrc
RUN sh -c . /.bashrc

#Start Tomcat on startup
WORKDIR /opt/apache-tomcat-7.0.73/bin
ENTRYPOINT ./startup.sh && tail -F /var/lib/tomcat/error.log

 

