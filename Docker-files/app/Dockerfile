From openjdk:11 AS BUILD_IMAGE

RUN apt update && apt install maven -y

WORKDIR /app

COPY ../../ .
RUN mvn clean install

From tomcat:9-jre11

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=BUILD_IMAGE app/target/*.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]

