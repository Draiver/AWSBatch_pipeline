pipeline {
    agent any

        stages {
        stage('Read data from AWS Batch') {
          steps {
                def job_queue_name = sh returnStdout: true, sh 'aws batch describe-job-queues --job-queues'
                env.job_queue_name = job_queue_name
            }
          }
        }