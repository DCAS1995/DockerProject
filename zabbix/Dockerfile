FROM ubuntu:16.0.4
MAINTAINER DanielS <dcas1995@gmail.com>

#Download and install MySQL

#Download and install Lampstack

#Download and install Zabbix
RUN wget http://repo.zabbix.com/zabbix/3.0/debian/pool/main/z/zabbix-release/zabbix-release_3.0-1+jessie_all.deb
RUN dpkg -i zabbix-release_3.0-1+jessie_all.deb
RUN apt-get update
RUN apt-get install -y zabbix-server-mysql php5-mysql zabbix-frontend-php
 

