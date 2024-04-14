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
        
        
        
    }
}