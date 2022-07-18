FROM maven:3-openjdk-18 as build

ADD . .
RUN mvn package -Dmaven.test.skip

FROM openjdk:18-alpine

RUN mkdir -p /app
WORKDIR /app

ARG JAR_FILE=target/*.jar
COPY --from=build ${JAR_FILE} app.jar

ENTRYPOINT [ "java", "-jar", "/app/app.jar" ]
