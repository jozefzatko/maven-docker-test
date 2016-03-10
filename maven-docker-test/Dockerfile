FROM java:8 

MAINTAINER Jozef Zatko <jozefzatko.sk@gmail.com>

# Install maven
RUN apt-get update
RUN apt-get install -y maven

WORKDIR /workspace

# Prepare by downloading dependencies
ADD pom.xml /workspace/pom.xml
RUN ["mvn", "dependency:resolve"]
RUN ["mvn", "verify"]

# Adding source, compile and package into a fat jar
ADD src /workspace/src
RUN ["mvn", "install"]

# Run application
ENTRYPOINT ["java", "-jar", "/workspace/target/maven-docker-test.jar"]
