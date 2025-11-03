#FROM openjdk:11
#COPY ./target/ms-client-0.0.1-SNAPSHOT.jar ms-client.jar
#ENTRYPOINT ["java","-jar","ms-client.jar"]

FROM maven:3.8.7-openjdk-11 AS build
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

FROM openjdk:11
WORKDIR /app
COPY --from=build /app/target/ms-client-0.0.1-SNAPSHOT.jar ms-client.jar
ENTRYPOINT ["java","-jar","ms-client.jar"]

