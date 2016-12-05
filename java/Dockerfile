#ocker file to deploy a Java application
FROM ubuntu:16.04
MAINTAINER DanielS

#et get and wget
RUN apt-get -y update
RUN apt-get install -y git
RUN apt-get install -y wget

#ownload and install the java tarball
RUN wget --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u5-b13/jdk-8u5-linux-x64.tar.gz 
RUN tar -zxvf jdk-8u5-linux-x64.tar.gz
RUN cp -r jdk1.8.0_05/ /opt
RUN update-alternatives --install /usr/bin/java java /opt/jdk1.8.0_05/bin/java 100
RUN update-alternatives --install /usr/bin/javac javac /opt/jdk1.8.0_05/bin/javac 100

#nstall maven
WORKDIR ~
RUN wget http://mirror.ox.ac.uk/sites/rsync.apache.org/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz
RUN tar zxvf apache-maven-3.3.9-bin.tar.gz
RUN cp -r apache-maven-3.3.9 /opt
RUN update-alternatives --install /usr/bin/mvn mvn /opt/apache-maven-3.3.9/bin/mvn 1
RUN mvn -version
