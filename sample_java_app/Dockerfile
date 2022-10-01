FROM tomcat
RUN apt-get update
RUN apt-get install git -y && \
	apt-get install xmlstarlet -y
RUN apt-get install default-jdk -y && \
	apt-get install maven -y
RUN git clone https://github.com/ashburnere/onlineshop-war.git /tmp/onlineshop-war
RUN xmlstarlet ed -N x="http://maven.apache.org/POM/4.0.0" \
 -s '/project/build' -t elem -n 'plugins' \
 -s '/project/build/plugins' -t elem 'plugin' \
 -s '/project/build/plugins/plugin' -t elem -n 'groupId' -v 'org.apache.maven.plugins' \
 -s '/project/build/plugins/plugin' -t elem -n 'artifactId' -v 'maven-war-plugin' \
 -s '/project/build/plugins/plugin' -t elem -n 'version' -v '3.3.2' \
 /tmp/onlineshop-war/pom.xml
RUN mvn package -f /tmp/onlineshop-war
RUN cp /tmp/onlineshop-war/target/*.war /usr/local/tomcat/webapps/
RUN rm -rf /tmp/onlineshop-war
