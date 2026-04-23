pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pulls code from the SCM defined in the job configuration 
                checkout scm
            }
        }

        stage('Build & Test') {
            steps {
                // Uses 'bat' for Windows Command Prompt 
                // 'mvn clean test' runs the full lifecycle including unit tests [cite: 278, 736]
                bat 'mvn clean test'
            }
        }
    }

    post {
        always {
            // Automatically finds and publishes JUnit test results [cite: 352, 800]
            junit '**/target/surefire-reports/*.xml'
        }
    }
}