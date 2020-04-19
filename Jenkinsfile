pipeline {
    agent any
    environment {
        CI = 'true'
        nodejs(nodeJSInstallationName: 'node12') 
    }
    stages {
        stage('Build') {
            steps {
                
                sh 'npm install'
            
           }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}
