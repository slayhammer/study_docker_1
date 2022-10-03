# This is a sample java app (https://github.com/ashburnere/onlineshop-war)
# wrapped in a docker container.
# Available at http://<your_address>:8080/onlineshop

# Based on 'ubuntu' ver. 20.04 Official Docker Image
FROM ubuntu:20.04

# Environment setup
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Moscow
ENV CATALINA_HOME /var/lib/tomcat9
ENV PATH $CATALINA_HOME/bin:$PATH

# Seting up all necessary software and further cache cleaning:
#	'git'         - for cloning the sample java app from a rep
#	'tomcat9'     - for hosting the app
#	'default-jdk' - maven prereq
#	'maven'       - for building the app
RUN apt-get update && apt-get install -y \
	git \
	tomcat9 \
	default-jdk \
	maven \
	&& rm -rf /var/lib/apt/lists/*	

# Fetching the sample java app src
RUN git clone https://github.com/ashburnere/onlineshop-war.git /tmp/onlineshop-war

# Building the app
RUN mvn package -f /tmp/onlineshop-war

# Installing the app on tomcat
RUN cp /tmp/onlineshop-war/target/*.war /var/lib/tomcat9/webapps/

# Cleaning src
RUN rm -rf /tmp/onlineshop-war

# Test tomcat
WORKDIR $CATALINA_HOME
RUN echo $PATH
RUN cat $CATALINA_HOME/bin/daemon.sh
RUN find / -type f -name "catalina.sh"
#RUN catalina.sh version

EXPOSE 8080

CMD ["catalina.sh", "run"]