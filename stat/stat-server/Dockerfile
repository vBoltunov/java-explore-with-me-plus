FROM eclipse-temurin:21-jdk-alpine
WORKDIR /app
COPY target/stat-server*.jar /app/stat-server.jar
CMD ["java", "-jar", "/app/stat-server.jar"]