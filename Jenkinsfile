pipeline {
    agent any

    stages {
        stage("build") {
            steps {
                // Echo a message indicating the build stage
                echo "this is build stage"
            }
        }
        stage('Clean Install') {
            steps {
                sh 'rm -rf node_modules package-lock.json'
                sh 'npm install'
            }
        }
    }
}