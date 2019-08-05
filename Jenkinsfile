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
          steps {        
              sh label: '', script: '''previous_job_status=$(curl -s http://admin:admin@localhost:8080/job/Test/job/Branch-1/lastBuild/api/json | jq -r \'.result\')
                while [ "$previous_job_status" == "null" ];
                do
                    previous_job_status=$(curl -s http://admin:admin@localhost:8080/job/Test/job/Branch-1/lastBuild/api/json | jq -r \'.result\')
                    echo "Waiting for job completion"
                    sleep 10
                done
                '''
              sh 'sleep 20'
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
          
