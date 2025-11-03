#FROM openjdk:11
#COPY ./target/ms-client-0.0.1-SNAPSHOT.jar ms-client.jar
#ENTRYPOINT ["java","-jar","ms-client.jar"]
# Etapa 1: build con Maven + OpenJDK 11 (UBI)
FROM registry.access.redhat.com/ubi8/openjdk-11 AS build
WORKDIR /app

# Copiamos el proyecto
COPY ms-client/ /app/

# Dar permisos al usuario no-root (UID 185 en UBI)
RUN chmod -R g+rwX /app

# Ejecutar build
RUN mvn clean package -DskipTests

# Etapa 2: runtime con OpenJDK 11 (UBI)
FROM registry.access.redhat.com/ubi8/openjdk-11-runtime
WORKDIR /app

# Copiamos el jar resultante desde la etapa anterior
COPY --from=build /app/target/ms-client-0.0.1-SNAPSHOT.jar ms-client.jar

# Puerto opcional (solo informativo)
# EXPOSE 8080

ENTRYPOINT ["java","-jar","ms-client.jar"]

