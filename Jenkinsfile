pipeline{
    agent any
    
    tools {nodejs "npm"}
    
    stages{
        stage("Cloning Github Repository"){
            //cloning code from github
            steps{
                git(url: 'https://github.com/flaseen/gallery.git', branch: 'master')
            }
        }
        
        stage("Installing Dependencies"){
            //installing app dependencies using npm
            steps{
                sh 'npm install'
            }
        }
        
        stage("Running Tests"){
            //running tests using npm
            steps{
                sh 'npm test'
            }
        }
    }
    
    post {
        success {
           slackSend channel: 'yakub_ip1', message: "${env.JOB_NAME} Build successful: ID:${env.BUILD_ID}";
        }
        failure {
            slackSend channel: 'yakub_ip1', message: "${env.JOB_NAME} Build failed: ID:${env.BUILD_ID}";
        }  
    }
}