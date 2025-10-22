# ---- build (Maven) ----
FROM maven:3.9-eclipse-temurin-21 AS build
WORKDIR /workspace
COPY . .
RUN mvn -f aluguel-ms/pom.xml -DskipTests=true clean package

# ---- runtime (JRE) ----
FROM eclipse-temurin:21-jre
WORKDIR /app
COPY --from=build /workspace/aluguel-ms/target/*.jar app.jar
ENV PORT=8080
EXPOSE 8080
CMD ["sh","-c","java -Dserver.port=${PORT} -jar app.jar"]
