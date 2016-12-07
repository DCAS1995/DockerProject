FROM ubuntu:16.04
MAINTAINER DanielS <dcas1995@gmail.com>

#Update the system
RUN apt-get update && \
apt-get install -y wget && \
apt-get install -y make && \
apt-get install -y gcc && \
apt-get install -y git && \
apt-get install -y libicu-dev

#Download postfix
WORKDIR /opt
RUN wget ftp://ftp.porcupine.org/mirrors/postfix-release/official/postfix-3.1.3.tar.gz
RUN tar zxvf postfix-3.1.3.tar.gz

#Pre-installation configuration. Adding users to their allocated groups
RUN groupadd -g 32 postfix && \
groupadd -g 31 postdrop && \
useradd -c "Postfix Daemon User" -d /var/spool/postfix -g postfix\
	-s /bin/false -u 32 postfix && \
chown -v postfix:postfix /var/mail

WORKDIR postfix-3.1.3
RUN sed -i 's/.\x08//g' README_FILES/*

RUN make makefiles CCARGS="-DNO_DB" && make

#RUN make install-postfix
RUN sh postfix-install -non-interactive \
daemon_directory=/usr/lib/postfix \
manpage_directory=/usr/share/man \
html_directory=/usr/share/doc/postfix-3.1.3/html \
readme_directory=/usr/share/doc/postfix-3.1.3/readme

WORKDIR /opt
RUN git clone https://github.com/DCAS1995/aliases.git
RUN mv aliases/aliases /etc

#WORKDIR /usr/ports/mail/postfix-current
#RUN make config
#RUN make install clean

#ENTRYPOINT /usr/sbin/postfix check && /usr/sbin/postfix start
