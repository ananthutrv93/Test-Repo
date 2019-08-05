pipeline {
    agent any
    options {
        disableConcurrentBuilds()
    }
    stages {
        stage('checkout') {
          steps {
            checkout scm
            }
        }
        stage('master') {
          when {
            branch 'master'
          }
          lock(inversePrecedence: true, resource: 'Master') {
            steps {        
              sh 'sleep 20'
            }
           }
        }
        stage('branch') {
          when {
            branch 'Branch-1'
          }
          steps {
            sh 'sleep 80'
          }
         }
     }
}
          
