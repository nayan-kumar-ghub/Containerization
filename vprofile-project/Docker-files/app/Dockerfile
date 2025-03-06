# Create a build image and copy src code
FROM maven:3.9.9-eclipse-temurin-21-jammy AS BUILD_IMAGE
LABEL "Project"="VProfile"
LABEL "Author"="Nayan"
WORKDIR /SRC
COPY src /SRC/src
COPY pom.xml /SRC/pom.xml
RUN mvn clean install

# Create a final image for deployment
FROM tomcat:10-jdk21
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE /vprofile-project/target/vprofile.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]