pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/yupaw17/jenkins-hw6.git'
            }
        }
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
        stage('Publish to Nexus') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'nexus-cred', usernameVariable: 'NEXUS_USER', passwordVariable: 'NEXUS_PASS')]) {
                    sh """
                        mvn deploy:deploy-file \
                          -DgroupId=com.example \
                          -DartifactId=helloworld \
                          -Dversion=1.0.0 \
                          -Dpackaging=jar \
                          -Dfile=target/helloworld-0.0.1-SNAPSHOT.jar \
                          -DrepositoryId=nexus \
                          -Durl=http://localhost:8081/repository/maven-releases/ \
                          -Dusername=$NEXUS_USER \
                          -Dpassword=$NEXUS_PASS
                    """
                }
            }
        }
    }
}
