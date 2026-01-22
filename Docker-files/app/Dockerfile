FROM maven:3.9.9-eclipse-temurin-21-jammy AS BUILD_IMAGE
RUN git clone git@github.com:Evandro-zigzig/vprofile-project.git
RUN cd vprofile-project && git checkout containers && mvn install

FROM tomcat:10-jdk21
RUN rm -rf /usr/local/tomcat/webapss/*
COPY --from=BUILD_IMAGE vprofile/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD [ "catalina.sh", "run" ]