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
    }
}
