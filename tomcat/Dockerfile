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

#Create user for tomcat
WORKDIR /opt/apache-tomcat-7.0.73/conf
RUN ls
RUN sed -i '37i <role rolename="manager-gui"/>' tomcat-users.xml
RUN sed -i '40i <user username="tomcat" password="pwd" roles="manager-gui,tomcat,role1"/>' tomcat-users.xml
RUN sed -i '38d' tomcat-users.xml
RUN cat -n tomcat-users.xml
#Start Tomcat on startup
WORKDIR /opt/apache-tomcat-7.0.73/bin
ENTRYPOINT ./startup.sh && tail -F /var/lib/tomcat/error.log

