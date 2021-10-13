pipeline {
  agent { label "master" }
  options {
    buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10'))
    skipStagesAfterUnstable()
  }
  parameters {
    choice (
      name: 'ENVIRONMENT',
      choices: ["partner-dev","travel-qa", "travel-prod", "travel-stage"],
      description: 'ENVIRONMENT'
    )
    string (
      name : 'INSTANCE_TYPE',
      defaultValue: 'kafka.m5.xlarge',
      description: 'INSTANCE_TYPE'
    )
  }
  stages {
    stage('CF Stack Opreation ') {
      steps {
          sh '''#!/bin/bash -xe
          CURRENT_DIRECTORY=`pwd`
          cd $CURRENT_DIRECTORY
          echo $INSTANCE_TYPE
          TEMPLATE_PATH=/var/jenkins_home/workspace/Test123/test.json

          #aws cloudformation create-stack --stack-name $STACK_NAME  --region $AWS_REGION  --template-body "file://"$TEMPLATE_PATH --parameters "file://parameters.json" --capabilities CAPABILITY_IAM --tags "Key"="Owner","Value"="Enablement" "Key"="CreatedBy","Value"="Jenkins" "Key"="Jenkins_Job","Value"="App-Services-Kafka-Setup"
          ls

          if ! aws cloudformation describe-stacks --region $AWS_REGION --stack-name $STACK_NAME ; then

           aws cloudformation create-stack --stack-name $STACK_NAME  --region $AWS_REGION  --template-body "file://"$TEMPLATE_PATH --parameters "file://parameters.json" --capabilities CAPABILITY_IAM --tags "Key"="Owner","Value"="Enablement" "Key"="CreatedBy","Value"="Jenkins" "Key"="Jenkins_Job","Value"="App-Services-Kafka-Setup"

           aws cloudformation wait stack-create-complete --stack-name $STACK_NAME --region $AWS_REGION

         else

           aws cloudformation update-stack --stack-name $STACK_NAME  --region $AWS_REGION  --template-body "file://"$TEMPLATE_PATH --parameters "file://parameters.json" --capabilities CAPABILITY_IAM

           aws cloudformation wait stack-update-complete --stack-name $STACK_NAME --region $AWS_REGION

         fi




          '''
      }
    }
  }
}
