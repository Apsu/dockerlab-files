# OpenStack client tools
# VERSION 0.1

FROM ubuntu:13.10

MAINTAINER Evan Callicoat <evan.callicoat@rackspace.com>

# Set the env variable DEBIAN_FRONTEND to noninteractive
ENV DEBIAN_FRONTEND noninteractive

# Add Havana Cloud-Archive repo and key
RUN echo "deb http://ubuntu-cloud.archive.canonical.com/ubuntu precise-updates/havana main" > /etc/apt/sources.list.d/cloud-archive.list
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EC4926EA

# Update repo data
RUN apt-get update

# Upgrade all the things
RUN apt-get dist-upgrade -y

# Install ssh and openstack-related clients
RUN apt-get install ssh mysql-client python-keystoneclient python-novaclient python-neutronclient python-glanceclient python-cinderclient -y

# Generate locale files
RUN locale-gen en_US.UTF-8

# Export it
ENV LANG en_US.UTF-8

# Prepare for sshd
RUN mkdir /var/run/sshd
RUN sed -i '/UsePAM/ s/yes/no/' /etc/ssh/sshd_config

# Open port
EXPOSE 22

# Authorize our key
ADD id_rsa.pub /root/.ssh/authorized_keys

# Start sshd
CMD ["/usr/sbin/sshd", "-D"]
