FROM maven:3-jdk-7

MAINTAINER Golfen Guo "golfen.guo@daocloud.io"

# Prepare by downloading dependencies
WORKDIR /code
ADD pom.xml /code/pom.xml
RUN mvn dependency:resolve

# Adding source, compile and package into a WAR
ADD src /code/src
RUN mvn -DskipTests=true package
RUN rm -rf /usr/local/tomcat/webapps/ROOT/*
RUN cp -r target/spring-boot-basewebapp-1.0/* $CATALINA_HOME/webapps/ROOT/

# Expose port
EXPOSE 8080

# Start WebApp
CMD ["mvn", "spring-boot:run"]
