pipeline {
    agent any
    
    tools {nodejs 'nodejs'}
    
    
    
    stages {
        stage ('Clone Respository') {
            steps {
                git branch: 'master', url:'https://github.com/Ian32-del/gallery'
            }
        }
        stage ('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage ('Testing') {
            steps {
                sh 'npm install'
            }
        }
        stage ('Send Slack Notification'){
            when {
                
                expression { currentBuild.result == 'SUCCESS'}
            }
            steps {
                script {
                    echo "Sending Slack notification . . ."
                    def buildId = env.BUILD_ID
                    def slackMessage = "Build #$buildId deployed successfully! "
                    slackSend(channel: '#jenkins', message:slackMessage)
                }
            }
        }
        post {
            failure {
                emailext attachLog: true,
                body: "Build failed for Job ${env.JOB_NAME}:${env.BUILD_NUMBER}. View console output at ${env.BUILD_URL}",
                subject: "Status: FAILURE - Job '${env.JOB_NAME}:${env.BUILD_NUMBER}'",
                to: 'ian.odhiambo@student.moringaschool.com'
            }
        }
        
        
        
    }
    
}