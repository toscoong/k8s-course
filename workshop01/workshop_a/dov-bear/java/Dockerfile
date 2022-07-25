# build
FROM maven:3-openjdk-18 AS build

WORKDIR /app

COPY . .
RUN mvn -f /app/pom.xml clean package

# run
FROM openjdk:3-openjdk-18-slim

COPY --from=build /app/dovbear-0.0.1-SNAPSHOT.jar /usr/local/lib/dovbear.jar

ENV PORT=5000
ENV INSTANCE_NAME="We Java Bears"
ENV INSTANCE_HASH="5jv2"

ENTRYPOINT ["java","-jar","/usr/local/lib/dovbear.jar"]
