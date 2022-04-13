# Build stage
FROM maven:3.8-jdk-11-slim AS build
WORKDIR /app
COPY . .
RUN mvn clean package

# Package stage
FROM openjdk:11-jre-slim
COPY --from=build /app/target/words-1.0-SNAPSHOT.jar /app/words.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/app/words.jar"]
