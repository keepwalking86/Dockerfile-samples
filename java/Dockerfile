FROM adoptopenjdk/openjdk11:jre-11.0.9.1_1-alpine

ENV TZ=Asia/Ho_Chi_Minh

RUN mkdir /config
RUN mkdir /logs

ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar

ENTRYPOINT ["java","-jar","/app.jar"]
