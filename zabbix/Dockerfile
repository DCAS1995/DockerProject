FROM ubuntu:mysql
MAINTAINER DanielS <dcas1995@gmail.com>

RUN apt-get update

RUN wget http://repo.zabbix.com/zabbix/3.0/debian/pool/main/z/zabbix-release/zabbix-release_3.0-1+jessie_all.deb

RUN dpkg -i zabbix-release_3.0-1+jessie_all.deb
RUN apt-get install -y zabbix-server-mysql zabbix-frontend-php
 

