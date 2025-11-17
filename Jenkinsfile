pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/yupaw17/jenkins-hw6.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'chmod +x mvnw'
                sh './mvnw clean package -DskipTests'
            }
        }

        stage('Publish to Nexus') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'nexus-cred', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh '''#!/bin/bash
                    ./mvnw deploy:deploy-file \
                    -DgroupId=com.example \
                    -DartifactId=spring-boot-complete \
                    -Dversion=0.0.1-SNAPSHOT \
                    -Dpackaging=jar \
                    -Dfile=target/spring-boot-complete-0.0.1-SNAPSHOT.jar \
                    -DrepositoryId=nexus \
                    -Durl=http://nexus3:8081/repository/maven-releases/ \
                    -Dusername=$USERNAME \
                    -Dpassword=$PASSWORD
                    '''
                }
            }
        }
    }
}
