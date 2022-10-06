# This is a sample java app setup package (https://github.com/ashburnere/onlineshop-war)
# wrapped in a docker container.

# Based on 'ubuntu' ver. 20.04 Official Docker Image
FROM ubuntu:20.04

# Environment setup
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Moscow

# Seting up all necessary software and further cache cleaning:
#	'git'         - for cloning the sample java app from a rep
#	'default-jdk' - maven prereq
#	'maven'       - for building the app
RUN apt-get update && apt-get install -y \
	git \
	default-jdk \
	maven \
	&& rm -rf /var/lib/apt/lists/*	

# Fetching the sample java app src
RUN git clone https://github.com/ashburnere/onlineshop-war.git /tmp/onlineshop-war

# Building the app
RUN mvn package -f /tmp/onlineshop-war
