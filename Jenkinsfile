pipeline {
    agent any

    stages {
        stage("build") {
            steps {
                // Echo a message indicating the build stage
                echo "this is build stage"
            }
        }
        stage('build') { 
            steps {
                sh 'npm install' 
            }
        }
    }
}