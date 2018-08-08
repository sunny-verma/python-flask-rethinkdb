# Dockerizing MongoDB: Dockerfile for building MongoDB images
# Based on ubuntu:latest, installs MongoDB following the instructions from:
# http://docs.mongodb.org/manual/tutorial/install-mongodb-on-ubuntu/

FROM       ubuntu:latest
MAINTAINER Docker

# Install RethinkDB.
RUN  apt-get update 
RUN apt-get install  -y wget
RUN echo "deb http://download.rethinkdb.com/apt `cat /etc/os-release | grep UBUNTU_CODENAME | cut -d '=' -f 2` main" > /etc/apt/sources.list.d/rethinkdb.list
RUN wget -O- http://download.rethinkdb.com/apt/pubkey.gpg | apt-key add - 
RUN  apt-get update 
RUN  apt-get install -y rethinkdb python-pip 
RUN  rm -rf /var/lib/apt/lists/*

# Install python driver for rethinkdb
RUN pip install rethinkdb

# Define mountable directories.
VOLUME ["/data"]

# Define working directory.
WORKDIR /data

# Define default command.
CMD ["rethinkdb", "--bind", "all"]

# Expose ports.
#   - 8080: web UI
#   - 28015: process
#   - 29015: cluster
EXPOSE 8080
EXPOSE 28015
EXPOSE 29015
