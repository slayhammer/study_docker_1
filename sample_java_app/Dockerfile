FROM tomcat
RUN apt-get update && apt-get install -y \
	git \
	xmlstarlet \
	default-jdk \
	maven -y \
	&& rm -rf /var/lib/apt/lists/*	
RUN git clone https://github.com/ashburnere/onlineshop-war.git /tmp/onlineshop-war
RUN cp -f /tmp/onlineshop-war/pom.xml /tmp/onlineshop-war/pom_orig.xml; \
	cat /tmp/onlineshop-war/pom_orig.xml | sed 's/xmlns=".*"//g' | \
	xmlstarlet ed -s '/project/build' -t elem -n 'plugins' \
	-s '/project/build/plugins' -t elem -n 'plugin' \
	-s '/project/build/plugins/plugin' -t elem -n 'groupId' -v 'org.apache.maven.plugins' \
	-s '/project/build/plugins/plugin' -t elem -n 'artifactId' -v 'maven-war-plugin' \
	-s '/project/build/plugins/plugin' -t elem -n 'version' -v '3.3.2' \
	 > /tmp/onlineshop-war/pom.xml; \
	 rm -f /tmp/onlineshop-war/pom_orig.xml; \
	 cat /tmp/onlineshop-war/pom.xml
# RUN mvn package -f /tmp/onlineshop-war
# RUN cp /tmp/onlineshop-war/target/*.war /usr/local/tomcat/webapps/
# RUN rm -rf /tmp/onlineshop-war
