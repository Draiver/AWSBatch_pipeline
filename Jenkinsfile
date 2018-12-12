#!/usr/bin/env groovy

pipeline {
    agent any
        
        stages {
            
        stage('Read data from AWS Batch') {
            when {
        // skip this stage unless branch is NOT master
             not {
              branch "master"
            }
        }
          steps {
              script {
                  def job_name = sh returnStdout: true, script: 'aws batch describe-job-queues --job-queues --region us-east-1'
                  env.job_name = job_name
                  def job_def = sh returnStdout: true, script: 'aws batch describe-job-definitions | jq -r \'.jobDefinitions[] | select(.status=="ACTIVE") | .jobDefinitionArn\''
                  env.job_def = job_def
                }
            }
        } 
        stage('Submit new job to AWS Batch') {
          steps {
              script {
                def job_name =  readJSON text: env.job_name
                job_name.jobQueues.each { jobQueue ->
                def job_id = sh returnStdout: true, script: "aws batch submit-job --job-name example --job-queue ${jobQueue.jobQueueName}  --job-definition ${env.job_def}"
                env.job_id = job_id 
                echo "${env.job_id}"
                }
                }
            }
        }
    }
}
