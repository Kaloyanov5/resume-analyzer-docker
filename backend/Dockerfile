# backend/Dockerfile
FROM openjdk:23-jdk-slim
VOLUME /tmp
WORKDIR /app
COPY target/resume-analyzer-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
