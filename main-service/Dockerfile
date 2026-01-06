FROM eclipse-temurin:21-jdk-alpine

WORKDIR /app

COPY target/main-service*.jar /app/ewm-service.jar

CMD ["java", "-jar", "/app/ewm-service.jar"]