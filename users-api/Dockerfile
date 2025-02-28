FROM maven:3.8.4-openjdk-8-slim AS build
WORKDIR /app

# Copy only pom.xml first
COPY pom.xml .
#COPY .mvn/ .mvn/
#COPY mvnw .
#COPY mvnw.cmd .

# Check if pom.xml exists before running Maven
RUN if [ -f "pom.xml" ]; then mvn dependency:go-offline -B; else echo "No pom.xml found, skipping dependency download"; fi



# Copy source code
COPY src ./src

# Build with caching enabled
RUN mvn package -DskipTests -B

# Run stage
FROM openjdk:8-jre-slim
WORKDIR /app

# Add a non-root user
RUN addgroup --system javauser && adduser --system --ingroup javauser javauser
USER javauser

COPY --from=build /app/target/users-api-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8083
ENTRYPOINT ["java", "-jar", "app.jar"]
