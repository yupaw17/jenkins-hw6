# Jenkins HW6: Spring Boot + GitHub + Nexus Integration

## Overview
This project demonstrates Jenkins integration with a Spring Boot HelloWorld app and Nexus artifact deployment.

## Structure
- `pom.xml` – Maven build file
- `src/` – Java source code
- `.mvn/` – Maven wrapper
- `Jenkinsfile` – Jenkins pipeline
- `README.md` – Project documentation

## Jenkins Pipeline
Stages:
1. Checkout from GitHub
2. Build with Maven
3. Deploy jar to Nexus

## Nexus Setup
- Nexus runs in Docker
- Hosted Maven repo: `maven-releases`
- Jenkins uses `nexus-cred` credentials

## How to Build
```bash
./mvnw clean package
# jenkins-hw6