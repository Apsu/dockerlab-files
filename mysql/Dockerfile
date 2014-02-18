# MySQL server
# VERSION 0.1

FROM ubuntu:12.04

MAINTAINER Evan Callicoat <evan.callicoat@rackspace.com>

EXPOSE 3306

VOLUME ["/var/lib/mysql"]

RUN apt-get update
RUN apt-get -y install mysql-server

ADD my.cnf /etc/mysql/my.cnf
ADD run /opt/run

CMD ["/opt/run"]
