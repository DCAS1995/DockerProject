FROM ubuntu:v2_java
MAINTAINER DanielS

#Update the system
RUN apt-get update
RUN apt-get install -y git

#Download the Jira bin file and change to an executable bin file
WORKDIR /opt
RUN wget https://www.atlassian.com/software/jira/downloads/binary/atlassian-jira-6.4.9-x64.bin
RUN chmod a+x atlassian-jira-6.4.9-x64.bin
RUN git clone https://github.com/DCAS1995/reponse.git
RUN mv reponse/response.varfile /opt
RUN ./atlassian-jira-6.4.9-x64.bin -q -varfile /opt/response.varfile

#Start Jira on startup of machine
WORKDIR /opt/atlassian/jira/bin
ENTRYPOINT ./start-jira.sh && tail -F /var/lib/jira/error.log

