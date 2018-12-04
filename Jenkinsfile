pipeline {
    agent any

        stages {
        stage('Read data from AWS Batch') {
          steps {
              script {
                  def job_queue = sh returnStdout: true, sh 'aws batch describe-job-queues --job-queues --region us-east-1'
                  env.job_queue = job_queue
                }
          }
          }
        }
}
