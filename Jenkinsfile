pipeline {
    agent any

        stages {
        stage('Read data from AWS Batch') {
          steps {
              script {
                  def job_queue = sh returnStdout: true, script: sh 'aws batch describe-job-queues --job-queues --region us-east-1'
                  env.job_queue = job_queue
                }
          }
          }
        stage('Read data from output') {
            steps {
                script {
                    def job_queue =  readJSON text: env.job_queue
                    sh 'aws batch submit-job --job-name $jobQueueName --job-queue HighPriority  --job-definition sleep60'  
                    }
           }
}
}
