# Use Maven with JDK 17 to build the app
FROM maven:3.9.6-eclipse-temurin-17 AS builder
WORKDIR /app

# Copy project files and build
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Use lightweight JDK image to run the app
FROM eclipse-temurin:17-jdk-jammy
WORKDIR /app

# Copy only the built jar from the builder stage
COPY --from=builder /app/target/*.jar app.jar

# Expose the default Spring Boot port
EXPOSE 8080

# Run the application
CMD ["java", "-jar", "app.jar"]
