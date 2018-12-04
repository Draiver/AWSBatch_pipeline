pipeline {
    agent any

        stages {
        stage('Read data from AWS Batch') {
          steps {
              sh 'aws batch describe-job-queues --job-queues --region us-east-1'
               }
          }
          }
        }
}
