pipeline {
    agent any

    tools {
        nodejs "NodeJS" // This should match the name you set in Global Tool Configuration
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Install Dependencies') {
            steps {
                // Install npm dependencies
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                // Run tests using Jest
                sh 'npm test'
            }
        }
        stage('Deploy') {
            // Example: Deploy only on main branch
            when {
                branch 'main'
            }
            steps {
                echo 'Deploying application...'
                // Insert your deployment commands here
            }
        }
    }
    
    post {
        always {
            // Archive test reports if you have them configured
            // If using jest-junit, for example:
            junit 'test-results.xml'
        }
    }
}
