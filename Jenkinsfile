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
                    def buildId = env.BUILD_ID
                    def slackMessage = "Build #$buildId deployed successfully! "
                    slackSend(channel: '#jenkins', message:slackMessage)
                }
            }
        }
        
        
        
    }
}