pipeline {
    agent any
    options {
        skipDefaultCheckout()
    }
    properties([
        [$class: 'BuildBlockerProperty',
        blockLevel: 'NODE',
        blockingJobs: '^test \\(pipeline\\)/.*',
        scanQueueFor: 'ALL',
        useBuildBlocker: true],
        disableConcurrentBuilds()
    ])
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
          steps {
            sh 'sleep 20'
          }
        }
        stage('branch') {
          when {
            branch 'Branch-1'
          }
          steps {
            sh 'sleep 20'
          }
         }
     }
}
          
