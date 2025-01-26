pipeline {
    agent any

    tools {
        nodejs "node" 
    }

    environment {
        EMAIL_RECIPIENT = 'lorraine.opiyo1@student.moringaschool.com'
        RENDER_DEPLOY_HOOK = 'https://api.render.com/deploy/srv-cub8uetds78s73aaolsg?key=HAofjRRtcW0'
    }

    triggers {
        githubPush() 
    }

    stages {
        stage("Clone Repository") {
            steps {
                git branch: "master", url: "https://github.com/OpiyoLorraine/gallery"
            }
        }

        stage("Install Dependencies") {
            steps {
                sh 'npm install'
            }
        }

        stage("Run Tests") {
            steps {
                sh 'npm test'
            }
        }

        stage("Deploy to Render") {
            steps {
                echo 'Deploying application to Render...'
                sh "curl -X POST ${RENDER_DEPLOY_HOOK}"
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!!'
        }
        failure {
            mail to: "${EMAIL_RECIPIENT}",
                 subject: 'Pipeline Failure Notification',
                 body: 'The pipeline failed at some stage. Please check Jenkins logs for details.'
        }
        always {
            echo 'Pipeline execution complete!!'

        }
        aborted {
            echo 'Pipeline execution aborted!!' 
        }
    }
}
