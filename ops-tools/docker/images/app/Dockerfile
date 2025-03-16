FROM maven:3.6.3-jdk-8 AS build
COPY ../../pom.xml /app/
COPY ../../src /app/src
WORKDIR /app
RUN mvn clean package -DskipTests

FROM openjdk:8-jdk-alpine
COPY --from=build /app/target/*.jar app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]