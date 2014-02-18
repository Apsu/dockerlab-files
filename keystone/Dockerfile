# OpenStack Keystone
# VERSION 0.1

FROM ubuntu:12.04

MAINTAINER Evan Callicoat <evan.callicoat@rackspace.com>

# Keystone service and admin API
EXPOSE 5000 35357

# Add Havana Cloud-Archive repo and key
RUN echo "deb http://ubuntu-cloud.archive.canonical.com/ubuntu precise-updates/havana main" > /etc/apt/sources.list.d/cloud-archive.list
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EC4926EA

# Update repo data
RUN apt-get update

# Install keystone and mysql module
RUN apt-get install keystone python-mysqldb -y

# Clear default SQLite DB
RUN rm /var/lib/keystone/keystone.db

# Add and set our script runner
ADD run /opt/run
CMD ["/opt/run"]
