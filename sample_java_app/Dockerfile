# This is a sample java app (https://github.com/ashburnere/onlineshop-war)
# wrapped in a docker container.
# Available at http://<your_address>:8080/onlineshop

# Based on 'tomcat' Official Docker Image
FROM ubuntu:20.04

# Seting up all necessary software and further cache cleaning:
#	'git'         - for cloning the sample java app from a rep
#	'xmlstarlet'  - for editing pom.xml file: add a current version of some plugin
#	'default-jdk' - maven prereq
#	'maven'       - for building the app
RUN apt-get update && apt-get install -y \
	git \
#	xmlstarlet \
	tomcat \
	default-jdk \
	maven \
	&& rm -rf /var/lib/apt/lists/*	

# Fetching the sample java app src
RUN git clone https://github.com/ashburnere/onlineshop-war.git /tmp/onlineshop-war

# Fixing pom.xml to add a current version of maven war plugin (as an existing one is too old for installed jdk)
#RUN cp -f /tmp/onlineshop-war/pom.xml /tmp/onlineshop-war/pom_orig.xml; \
#	cat /tmp/onlineshop-war/pom_orig.xml | sed 's/xmlns=".*"//g' | \
#	xmlstarlet ed -s '/project/build' -t elem -n 'plugins' \
#	-s '/project/build/plugins' -t elem -n 'plugin' \
#	-s '/project/build/plugins/plugin' -t elem -n 'groupId' -v 'org.apache.maven.plugins' \
#	-s '/project/build/plugins/plugin' -t elem -n 'artifactId' -v 'maven-war-plugin' \
#	-s '/project/build/plugins/plugin' -t elem -n 'version' -v '3.3.2' \
#	 > /tmp/onlineshop-war/pom.xml; \
#	 rm -f /tmp/onlineshop-war/pom_orig.xml

# Building the app
RUN mvn package -f /tmp/onlineshop-war

# Installing the app on tomcat
RUN cp /tmp/onlineshop-war/target/*.war /var/lib/tomcat/webapps/

# Cleaning src
RUN rm -rf /tmp/onlineshop-war

EXPOSE 8080

CMD ["catalina.sh", "run"]