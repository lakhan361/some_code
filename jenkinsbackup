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
  }
  stages {
    stage('CF Stack Opreation ') {
      steps {
          sh '''#!/bin/bash -xe
          CURRENT_DIRECTORY=`pwd`
          cd $CURRENT_DIRECTORY

          TEMPLATE_PATH=/var/jenkins_home/workspace/Test123/test.json

          PARAMETERS_PATH=test_parameters.json
asddasda
          envsubst < ${PARAMETERS_PATH} > parameters.json

          cat parameters.json

          #aws cloudformation create-stack --stack-name $STACK_NAME  --region $AWS_REGION  --template-body "file://"$TEMPLATE_PATH --parameters "file://parameters.json" --capabilities CAPABILITY_IAM 
          ls

          if ! aws cloudformation describe-stacks --region $AWS_REGION --stack-name $STACK_NAME ; then

           aws cloudformation create-stack --stack-name $STACK_NAME  --region $AWS_REGION  --template-body "file://"$TEMPLATE_PATH --parameters "file://parameters.json" --capabilities CAPABILITY_IAM 

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
