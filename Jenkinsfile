pipeline {
    agent any

    stages {
        stage("build") {
            steps {
                // Echo a message indicating the build stage
                echo "this is build stage"
            }
        }
        stage("install dependencies") {
            steps {
                sh 'npm install'
            }
        }
    }
}