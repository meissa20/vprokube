FROM maven:3.10-eclipse-temurin-21-noble AS builder
ENV MAVEN_OPTS="-Xms256m -Xmx2048m"
RUN git clone https://github.com/hkhcoder/vprofile-project.git
RUN cd vprofile-project && git checkout containers && mvn install -DskipTests

FROM tomcat:11.0-jdk21-temurin-noble
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=builder /vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/

EXPOSE 8080
CMD ["catalina.sh", "run"]
