pipeline {
    agent any  // Use any available Jenkins agent to run this pipeline

    environment {
        // Optional: You can set environment variables like MongoDB Atlas credentials here
        MONGO_USER = 'lorraine123'  // Replace with your MongoDB Atlas username
        MONGO_PASSWORD = 'lorraine123'  // Replace with your MongoDB Atlas password
    }

    stages {
        // Stage to install dependencies
        stage('Install Dependencies') {
            steps {
                script {
                    // Run npm install to install required dependencies
                    sh 'npm install'
                }
            }
        }

        // Stage to run tests (optional)
        stage('Run Tests') {
            steps {
                script {
                    // Check if tests exist, then run them
                    if (fileExists('tests')) {
                        sh 'npm test'
                    } else {
                        echo "No tests found. Skipping test stage."
                    }
                }
            }
        }

        // Stage to deploy the app to Render
        stage('Deploy to Render') {
            steps {
                script {
                    // Make sure the application is running before deploying (if applicable)
                    sh 'node server.js'  // Adjust if your server start command is different
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful!!!'
        }

        failure {
            echo 'Deployment Failed!!!'
        }
    }
}
