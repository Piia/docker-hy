FROM openjdk
COPY . .
EXPOSE 8080
RUN ./mvnw package
ENTRYPOINT java -jar ./target/docker-example-1.1.3.jar