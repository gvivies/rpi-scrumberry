# MongoDB Dockerfile for Scrumberry

# Pull base image.
FROM resin/rpi-raspbian

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update

# Install packages
RUN apt-get install -y mongodb-server

# Create database directory
RUN mkdir -p /data/db

# Expose MongoDB port
EXPOSE 27017
EXPOSE 28017

# Define default command.
CMD ["/usr/bin/mongod","--smallfiles"]
