FROM ubuntu:v2_java
MAINTAINER DanielS <dcas1995@gmail.com>

RUN apt-get update

#Download and unpackage the nexus tarball
WORKDIR /opt
RUN wget http://download.sonatype.com/nexus/3/nexus-3.0.2-02-unix.tar.gz
RUN tar zxvf nexus-3.0.2-02-unix.tar.gz

#Create symbolic link for nexus
WORKDIR /usr/bin
RUN ln -s /opt/nexus-3.0.2-02 nexus

#Launch nexus on startup of container
WORKDIR /opt/nexus-3.0.2-02/bin
ENTRYPOINT ./nexus run && tail -F /var/lib/nexus/error.log
