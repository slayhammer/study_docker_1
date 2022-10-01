FROM tomcat
RUN apt-get update
RUN apt-get install git -y && \
	apt-get install xmlstarlet -y
RUN apt-get install default-jdk -y && \
	apt-get install maven -y
RUN git clone https://github.com/ashburnere/onlineshop-war.git /tmp/onlineshop-war
RUN /bin/bash -c "cat /tmp/onlineshop-war/pom.xml | sed '2 s/xmlns=".*"//g' | xmlstarlet ed -s '/project/build' -t elem -n 'plugins' \
 -s '/project/build/plugins' -t elem -n 'plugin' \
 -s '/project/build/plugins/plugin' -t elem -n 'groupId' -v 'org.apache.maven.plugins' \
 -s '/project/build/plugins/plugin' -t elem -n 'artifactId' -v 'maven-war-plugin' \
 -s '/project/build/plugins/plugin' -t elem -n 'version' -v '3.3.2'"
RUN mvn package -f /tmp/onlineshop-war
RUN cp /tmp/onlineshop-war/target/*.war /usr/local/tomcat/webapps/
RUN rm -rf /tmp/onlineshop-war
