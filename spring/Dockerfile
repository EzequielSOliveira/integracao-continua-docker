FROM maven:3.8.6-openjdk-18 AS maven
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src src
RUN mvn dependency:resolve-plugins dependency:resolve package
FROM openjdk:latest
EXPOSE 9000
CMD java -jar /data/sgcmapi.jar
COPY --from=maven /target/sgcmapi.jar /data/sgcmapi.jar
