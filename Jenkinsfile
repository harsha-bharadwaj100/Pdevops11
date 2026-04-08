pipeline {
    agent any
    tools {
        jdk 'JDK21'    // Must match the name in Jenkins Global Tool Configuration
        maven 'Maven3' // Must match the name in Jenkins Global Tool Configuration
    }
    stages {
        stage('Checkout') {
            steps {
                // Jenkins will pull your code from the GitHub URL you provide in the UI
                checkout scm 
            }
        }
        stage('Build & Test') {
            steps {
                // Using 'bat' because your Jenkins is running on Windows
                bat 'mvn clean test' 
            }
        }
    }
    post {
        always {
            // This publishes the XML results to the Jenkins UI [cite: 114]
            junit '**/target/surefire-reports/*.xml' 
        }
    }
}
