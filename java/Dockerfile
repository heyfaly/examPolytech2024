FROM maven:3.9-eclipse-temurin-8 AS builder

LABEL maintainer="faly"

WORKDIR /app

COPY . .

RUN mvn clean package -DskipTests


FROM eclipse-temurin:8-jre

EXPOSE 8448

COPY --from=builder /app/target/java-*.jar back.jar

CMD ["java", "-jar", "back.jar"]

