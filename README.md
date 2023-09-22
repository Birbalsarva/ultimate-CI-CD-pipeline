# ultimate-CI-CD-pipeline

This project demonstrates an ultimate CI/CD pipeline for a Spring Boot application using Jenkins, Docker, Maven, and Kubernetes. The pipeline includes various stages, such as building, testing, static code analysis, building and pushing Docker images, and updating deployment files.

## Project Structure

The project structure is as follows:

- `src/main/java/com/abhishek`: This directory contains the Java source code for the Spring Boot application.
- `resources`: This directory contains application configuration files.
- `Dockerfile`: The Dockerfile for building the Docker image of the application.
- `Jenkinsfile`: The Jenkins pipeline code defining the CI/CD process.
- `deployment.yml`: Kubernetes Deployment file for deploying the application.
- `service.yml`: Kubernetes Service file for exposing the application.

## Jenkins Pipeline

The Jenkins pipeline is defined in the `Jenkinsfile` and consists of the following stages:

1. **Checkout**: Clones the project repository from GitHub.

2. **Build and Test**: Compiles the Java code, packages the application into a JAR file, and runs tests.

3. **Static Code Analysis**: Performs static code analysis using SonarQube.

4. **Build and Push Docker Image**: Builds a Docker image from the application and pushes it to a Docker registry (Docker Hub).

5. **Update Deployment File**: Updates the Kubernetes deployment file with the new Docker image tag and pushes the changes to the GitHub repository.

## Dockerfile

The `Dockerfile` is used to build a Docker image for the Spring Boot application. It starts with the AdoptOpenJDK 11 Alpine base image, copies the JAR file into the image, and sets the entry point to run the application.

```Dockerfile
FROM adoptopenjdk/openjdk11:alpine-jre

# Specify the artifact path
ARG artifact=target/spring-boot-web.jar

WORKDIR /opt/app

COPY ${artifact} app.jar

# This should not be changed
ENTRYPOINT ["java","-jar","app.jar"]
```

## Deployment Files

- `deployment.yml`: This Kubernetes Deployment file defines the deployment for the Spring Boot application. It specifies the number of replicas and the Docker image to use.

- `service.yml`: This Kubernetes Service file defines a NodePort service to expose the application.

Feel free to modify and enhance this project according to your requirements. For any questions or issues, please open an [issue](https://github.com/Birbalsarva/ultimate-CI-CD-pipeline/issues) or reach out to the project contributors. Happy coding!

**Note:** Make sure to replace placeholder values and customize the files to match your project's specifics.
