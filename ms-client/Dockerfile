#FROM openjdk:11
#COPY ./target/ms-client-0.0.1-SNAPSHOT.jar ms-client.jar
#ENTRYPOINT ["java","-jar","ms-client.jar"]

FROM registry.access.redhat.com/ubi8/openjdk-11 AS build
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

FROM registry.access.redhat.com/ubi8/openjdk-11-runtime
#WORKDIR /app

COPY --from=build /app/target/ms-client-0.0.1-SNAPSHOT.jar ms-client.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","ms-client.jar"]

