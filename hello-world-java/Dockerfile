#Build JAR file
FROM maven:3.6.3 AS stage1
WORKDIR /home/app
COPY . /home/app/
RUN mvn -f /home/app/pom.xml clean package

#Create an image
FROM openjdk:8-jdk-alpine 
EXPOSE 5005
COPY --from=stage1 /home/app/target/hello-world-java.jar hello-world-java.jar
ENTRYPOINT [ "sh", "-c", "java -jar /hello-world-java.jar" ]

