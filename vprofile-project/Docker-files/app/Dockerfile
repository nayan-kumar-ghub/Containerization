# Create a build image and copy src code
FROM maven:3.9.9-eclipse-temurin-21-jammy AS build_image
LABEL "Project"="VProfile"
LABEL "Author"="Nayan"
WORKDIR /SRC
COPY pom.xml .
COPY src/ src/
RUN MAVEN_OPTS="-Xmx1024m" mvn clean package
RUN ls -l /SRC/target

# Create a final image for deployment
FROM tomcat:9-jre11
LABEL "Project"="VProfile"
LABEL "Author"="Nayan"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=build_image /SRC/target/vprofile.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
