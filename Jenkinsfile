pipeline {
    agent any
    tools {
        jdk 'JDK21' 
        maven 'Maven3'
    }
    stages {
        stage('Build & Test') {
            steps {
                bat 'mvn clean test' 
            }
        }
        stage('Docker Build & Run') {
            steps {
                bat 'docker build -t calculator-app .'
                bat 'docker run --rm calculator-app'
            }
        }
    }
    post {
        always {
            junit '**/target/surefire-reports/*.xml'
            archiveArtifacts artifacts: 'target/site/jacoco/**', fingerprint: true
        }
    }
}
