pipeline {
    agent any

    environment {
        NODEJS_HOME = tool 'NodeJS 23.7.0' // Use the Node.js environment from Jenkins
        PATH = "${NODEJS_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/PadalaDevisrisairam/sasi-converter.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Post-Test Results') {
            steps {
                junit 'jest-results.xml'
            }
        }
    }

    post {
        success {
            echo 'Tests passed successfully!'
        }
        failure {
            echo 'Tests failed. Check logs.'
        }
    }
}

