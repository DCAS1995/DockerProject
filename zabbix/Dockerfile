FROM ubuntu:16.04
MAINTAINER DanielS <dcas1995@gmail.com>

#Download and install the dependencies for Zabbix
RUN apt-get update && \
 apt-get install -y apache2 &&\
 apt-get install -y wget 

RUN echo 'mysql-server mysql-server/root_password password 123'| debconf-set-selections
RUN echo 'mysql-server mysql-server/root_password_again password 123'|debconf-set-selections
RUN apt-get install -y mysql-server
RUN apt-get install -y php7.0 php7.0-cli php7.0-common php7.0-mysql libapache2-mod-php7.0\
 php7.0-cgi php7.0-xmlreader php7.0-xmlwriter php7.0-bcmath php7.0-mbstring


#Download and install Zabbix
WORKDIR /opt
RUN wget http://repo.zabbix.com/zabbix/3.2/ubuntu/pool/main/z/zabbix-release/zabbix-release_3.2-1+xenial_all.deb
RUN dpkg -i zabbix-release_3.2-1+xenial_all.deb
RUN apt-get update
RUN apt-get install -q -y zabbix-server-mysql zabbix-frontend-php

#Set timezone for the apache server
RUN sed -i '/;date.timezone =/c\date.timezone = UTC' /etc/php/7.0/apache2/php.ini

#Create database schema
RUN service mysql start \
&& mysql -u root -p123 -e "create user zabbix;" \
&& mysql -u root -p123 -e "create database zabbixdb;" \
&& mysql -u root -p123 -e "grant all on zabbixdb.* to zabbix@localhost identified by '123';" \
&& mysql -u root -p123 -e "flush privileges;"

WORKDIR /usr/share/doc/zabbix-server-mysql
RUN service mysql start && zcat create.sql.gz | mysql zabbixdb -u zabbix -p123

#Update zabbix server config file
RUN sed -i '82i DBHost=localhost' /etc/zabbix/zabbix_server.conf
RUN sed -i '92i DBName=zabbixdb' /etc/zabbix/zabbix_server.conf
RUN sed -i '93d' /etc/zabbix/zabbix_server.conf
RUN sed -i '108i DBUser=zabbix' /etc/zabbix/zabbix_server.conf
RUN sed -i '109d' /etc/zabbix/zabbix_server.conf
RUN sed -i '117i DBPassword=123' /etc/zabbix/zabbix_server.conf
RUN sed -i '132d ' /etc/zabbix/zabbix_server.conf
RUN sed -i '132i DBPort=3306' /etc/zabbix/zabbix_server.conf

#restart servers and start everything up on boot
#RUN cat -n /etc/zabbix/zabbix_server.conf
RUN service apache2 restart && service zabbix-server restart 
ENTRYPOINT service apache2 start && service zabbix-server start && service mysql start && bash
