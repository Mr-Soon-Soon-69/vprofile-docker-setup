# pull image that combine ubuntu+jdk+maven
FROM maven:3.9.9-eclipse-temurin-21-jammy AS build_tools
RUN git clone -b docker https://github.com/hkhcoder/vprofile-project.git
WORKDIR vprofile-project/
RUN mvn install


FROM tomcat:10-jdk21
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=build_tools vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]