pipeline {
    agent any

    environment {
        NODEJS_HOME = tool 'NodeJS'
        PATH = "${NODEJS_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/PadalaDevisrisairam/sasi-converter.git' // Replace with your repo URL
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

        stage('Build') {
            steps {
                sh 'npm run build' // If applicable
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying the application..."
                // Add deployment commands if necessary
            }
        }
    }

    post {
        always {
            echo "Pipeline Execution Completed"
        }
        success {
            echo "Pipeline ran successfully!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}
