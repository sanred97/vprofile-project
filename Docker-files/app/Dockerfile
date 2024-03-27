FROM openjdk:11 AS BUILD_IMAGE
LABEL "project"="vprofile"
LABEL "Author"="minski"
RUN apt update && apt install git maven -y
RUN git clone https://github.com/sanred97/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat;
LABEL "project"="vprofile"
LABEL "Author"="minski"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh","run"]