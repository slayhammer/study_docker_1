# This is a sample java app runtime package (https://github.com/ashburnere/onlineshop-war)
# wrapped in a docker container.
# Available at http://<your_address>:8080/onlineshop

# Based on 'ubuntu' ver. 20.04 Official Docker Image
FROM ubuntu:20.04

# Environment setup
ARG DEBIAN_FRONTEND=noninteractive
ARG catalina-base
ARG catalina-home
ENV TZ=Europe/Moscow
ENV CATALINA_HOME $catalina-home
ENV CATALINA_BASE $catalina-base
ENV PATH $CATALINA_HOME/bin:$CATALINA_BASE/bin:$PATH

# Seting up all necessary software and further cache cleaning:
#	'tomcat9'     - for hosting the app

RUN apt-get update && apt-get install -y \
	tomcat9 \
	&& rm -rf /var/lib/apt/lists/*	

# Running environment
EXPOSE 8080
CMD ["catalina.sh", "run"]