FROM tomcat
RUN apt-get update
RUN apt-get install default-jdk -y
RUN apt-get install maven -y
RUN git clone https://github.com/ashburnere/onlineshop-war.git /tmp
RUN mvn package -f /tmp/onlineshop-war
RUN cp /tmp/onlineshop-war/target/*.war /usr/local/tomcat/webapps/
RUN rm -rf /tmp/onlineshop-war
