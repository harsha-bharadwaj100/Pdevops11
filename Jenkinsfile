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
    }
    post {
        always {
            junit '**/target/surefire-reports/*.xml'
            archiveArtifacts artifacts: 'target/site/jacoco/**', fingerprint: true
        }
    }
}
