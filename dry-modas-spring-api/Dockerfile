FROM maven:3.9.4-eclipse-temurin-17 AS builder
WORKDIR /app

COPY pom.xml .
RUN mvn dependency:go-offline

COPY src ./src
RUN mvn clean package -DskipTests

FROM eclipse-temurin:17-jdk-jammy
WORKDIR /app

COPY --from=builder /app/target/*.jar app.jar

EXPOSE 5001

ENTRYPOINT ["java", "-jar", "app.jar"]
