pipeline {
  agent { label "master" }
  parameters {
    string (
      name : 'S3_BUCKET',
      defaultValue: '',
      description: 'Bucket_name.'
    )
    string (
      name : 'ROLE_ARN',
      defaultValue: '',
      description: 'Role for the task.'
    )
  }
  stages {
    stage('Automation') {
      steps {
          sh '''#!/bin/bash -xe

                aws sts assume-role --role-arn $ROLE_ARN --role-session-name TemporarySessionKeys --output json > assume-role-output.json
                AWS_ACCESS_KEY_ID=$(jq .Credentials.AccessKeyId assume-role-output.json)
                AWS_SECRET_ACCESS_KEY=$(jq .Credentials.SecretAccessKey assume-role-output.json)
                AWS_SESSION_TOKEN=$(jq .Credentials.SessionToken assume-role-output.json)


                export AWS_ACCESS_KEY_ID="${AWS_ACCESS_KEY_ID:1:-1}"
                export AWS_SECRET_ACCESS_KEY="${AWS_SECRET_ACCESS_KEY:1:-1}"
                export AWS_SESSION_TOKEN="${AWS_SESSION_TOKEN:1:-1}"

                aws s3 rm s3://$S3_BUCKET/ --recursive --exclude "*" --include "log-*"

                unset AWS_ACCESS_KEY_ID
                unset AWS_SECRET_ACCESS_KEY
                unset AWS_SESSION_TOKEN
          '''
      }
    }
  }
}
