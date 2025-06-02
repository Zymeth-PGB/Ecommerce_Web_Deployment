## build stage ##
FROM maven:3.6.3-openjdk-17-slim AS build

WORKDIR /app
COPY . .

RUN mvn install -DskipTests=true
## run stage ##
FROM eclipse-temurin:17-jre-alpine

WORKDIR /run
COPY --from=build /app/target/server-0.0.1-SNAPSHOT.jar .

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "server-0.0.1-SNAPSHOT.jar"]
