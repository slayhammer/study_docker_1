FROM tomcat
RUN apt-get update && apt-get install -y \
	bash \
	git \
	xmlstarlet \
	default-jdk \
	maven -y \
&& rm -rf /var/lib/apt/lists/*	
RUN git clone https://github.com/ashburnere/onlineshop-war.git /tmp/onlineshop-war
RUN ["/bin/bash", "-c", "cat /tmp/onlineshop-war/pom.xml | sed '2 s/xmlns=".*"//g'"]
# RUN mvn package -f /tmp/onlineshop-war
# RUN cp /tmp/onlineshop-war/target/*.war /usr/local/tomcat/webapps/
# RUN rm -rf /tmp/onlineshop-war
