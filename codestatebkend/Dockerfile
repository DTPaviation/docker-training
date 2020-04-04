FROM openjdk:11.0.6-jdk
# Add a volume pointing to /tmp
VOLUME /tmp
# Make port 8080 available to the world outside this container
EXPOSE 8080
# copy the source code
COPY codestatebkend/ ./
# give permission to run maven
RUN chmod +x ./mvnw
# invoke the maven build
RUN ./mvnw clean package
# The application's jar file (when packaged)
ARG JAR_FILE=codestatebkend/target/codestatebkend-0.0.1-SNAPSHOT.jar
# Add the application's jar to the container
ADD ${JAR_FILE} codestatebkend.jar
# Run the jar file 
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/codestatebkend.jar"]
