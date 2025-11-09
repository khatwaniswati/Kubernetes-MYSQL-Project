FROM maven:3.8.3-openjdk-17

WORKDIR /app

#COPY ./target/Kubernetes-Project-0.0.1-SNAPSHOT.jar .
#
#EXPOSE 8080
#
#CMD ["java", "-jar", "Kubernetes-Project-0.0.1-SNAPSHOT.jar"]

COPY .mvn/ .mvn
COPY mvnw pom.xml ./
RUN ./mvnw dependency:go-offline

COPY src ./src

CMD ["./mvnw", "spring-boot:run"]