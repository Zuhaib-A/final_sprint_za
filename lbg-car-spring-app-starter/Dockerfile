# Use an official Maven image as the build stage
FROM maven:3.8.4-openjdk-11 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy the Maven Wrapper files into the container
COPY mvnw mvnw.cmd .mvn/ ./

# Copy the project configuration files (pom.xml and settings.xml, if needed)
COPY pom.xml .

# Resolve and download project dependencies using the Maven Wrapper
RUN ./mvnw dependency:go-offline

# Copy the rest of the application source code
COPY src/ ./src/

# Build the Spring Boot application
RUN ./mvnw package -DskipTests

# Use an official OpenJDK image as the runtime stage
FROM openjdk:11-jre-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the built JAR file from the build stage into the runtime stage
COPY --from=build /app/target/*.jar ./app.jar

# Define the command to run the Spring Boot application
CMD ["java", "-jar", "app.jar"]