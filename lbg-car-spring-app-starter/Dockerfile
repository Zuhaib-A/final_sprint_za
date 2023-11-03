# Use an official Maven image to build the Spring Boot application
FROM maven:3.8.4-openjdk-11 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy the project source code and pom.xml into the container
COPY . .

# Build the Spring Boot application using Maven
RUN mvn package -DskipTests

# Use an official OpenJDK image as the runtime stage
FROM openjdk:11-jre-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the built JAR file from the build stage into the runtime stage
COPY --from=build /app/target/*.jar ./app.jar

# Define the command to run the Spring Boot application
CMD ["java", "-jar", "app.jar"]