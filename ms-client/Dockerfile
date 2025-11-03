#FROM openjdk:11
#COPY ./target/ms-client-0.0.1-SNAPSHOT.jar ms-client.jar
#ENTRYPOINT ["java","-jar","ms-client.jar"]
# Etapa 1: build con Maven + OpenJDK 11 (UBI)
# Etapa 1: build con Maven y OpenJDK 11
FROM registry.access.redhat.com/ubi8/openjdk-11 AS build

# Crea el directorio de trabajo y copia el código fuente
WORKDIR /app
COPY . .

# Ejecuta el build de Maven
RUN mvn clean package -DskipTests

# Etapa 2: runtime con OpenJDK 11
FROM registry.access.redhat.com/ubi8/openjdk-11-runtime
WORKDIR /app

# Copia el JAR generado desde la etapa de build
COPY --from=build /app/target/ms-client-0.0.1-SNAPSHOT.jar /app/ms-client.jar

# Define el comando de arranque
ENTRYPOINT ["java","-jar","/app/ms-client.jar"]

