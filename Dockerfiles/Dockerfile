FROM openjdk:8 AS BUILD_IMAGE
RUN apt-get update && apt-get install maven -y
#RUN git clone https://github.com/sriuday19/vprofile-ci-docker.git
ADD ../../ vprofile-docker
RUN cd vprofile-docker && mvn install

FROM tomcat:8-jre11
LABEL Author="uday"
LABEL project="vprofile"

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=BUILD_IMAGE vprofile-docker/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080

CMD [ ""catalina.sh", "run"" ]