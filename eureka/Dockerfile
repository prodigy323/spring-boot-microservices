FROM openjdk:8-jdk-alpine
ARG JAR_FILE
ARG SPRING_PROFILES_ACTIVE
COPY ${JAR_FILE} app.jar
ENV SPRING_PROFILES_ACTIVE=${SPRING_PROFILES_ACTIVE}
EXPOSE 8761
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","-Dspring.profiles.active=${SPRING_PROFILES_ACTIVE}","/app.jar"]