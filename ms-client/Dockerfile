#FROM openjdk:11
#COPY ./target/ms-client-0.0.1-SNAPSHOT.jar ms-client.jar
#ENTRYPOINT ["java","-jar","ms-client.jar"]

# Etapa 1: build con Maven + OpenJDK 11 (UBI)
FROM registry.access.redhat.com/ubi8/openjdk-11 AS build
WORKDIR /app
COPY ms-client/ /app/
RUN mvn clean package -DskipTests

# Etapa 2: runtime con OpenJDK 11 (UBI)
FROM registry.access.redhat.com/ubi8/openjdk-11-runtime
WORKDIR /app

COPY --from=build /app/target/ms-client-0.0.1-SNAPSHOT.jar ms-client.jar
#EXPOSE 8080
ENTRYPOINT ["java","-jar","ms-client.jar"]

