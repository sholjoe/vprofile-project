# Use openjdk as base image for the build stage
FROM openjdk:11 AS BUILD_IMAGE

# Install Maven
RUN apt update && apt install maven -y

# Clone the project and switch to the 'docker' branch
RUN git clone https://github.com/sholjoe/vprofile-project.git
RUN cd vprofile-project && git checkout docker

# Build the project using Maven
RUN cd vprofile-project && mvn install

# Use Tomcat as base image for the final stage
FROM tomcat:9-jre11 

# Remove the default ROOT application
RUN rm -rf /usr/local/tomcat/webapps/*

# Copy the built WAR file from the build stage to the webapps directory of Tomcat
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

# Expose port 8080
EXPOSE 8080

# Start Tomcat
CMD ["catalina.sh", "run"]

