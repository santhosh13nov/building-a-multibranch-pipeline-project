pipeline {
    agent any
    environment {
        CI = 'true'
         
    }
    stages {
        stage('Build') {
            steps {
                nodejs(nodeJSInstallationName: 'node12') {
                sh 'npm install'
                }
           }
        }
        stage('Test') {
            steps {
                nodejs(nodeJSInstallationName: 'node12') {
                sh './jenkins/scripts/test.sh'
            }
           }
        }
        stage('Deliver for development') {
            when {
                branch 'development' 
            }
            steps {
                nodejs(nodeJSInstallationName: 'node12') {
                sh './jenkins/scripts/deliver-for-development.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
           }     
        }
        stage('Deploy for production') {
            when {
                branch 'production'  
            }
            steps {
                nodejs(nodeJSInstallationName: 'node12') {
                sh './jenkins/scripts/deploy-for-production.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
           }     
        }
    }
}
