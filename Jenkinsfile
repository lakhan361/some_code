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
   name : 'STACK_NAME',
   defaultValue: 'aws-ElastiCache',
   description: 'Test'
   )

    string (
   name : 'cacheinstancetype',
   defaultValue: 'cache.t2.micro',
   description: 'INSTANCE_TYPE'
 )

   string (
  name : 'num_node_groups',
  defaultValue: '1',
  description: 'num_node_groups'
  )

  string (
 name : 'atrestencryptionenabled',
 defaultValue: 'true',
 description: 'num_node_groups'
 )

 string (
name : 'cachetype',
defaultValue: 'redis',
description: 'cachetype'
)
string (
name : 'transitencryptionenabled',
defaultValue: 'true',
description: 'transitencryptionenabled'
)

string (
name : 'cacheengineversion',
defaultValue: '5.0.6',
description: 'cacheengineversion'
)

string (
name : 'vpc_id',
defaultValue: 'vpc-0a1497dbb91dd4924',
description: 'vpc_id'
)

string (
name : 'snapshot_retention_limit',
defaultValue: '0',
description: 'snapshot_retention_limit'
)

string (
name : 'cacheport',
defaultValue: '6379',
description: 'cacheport'
)

string (
name : 'cachesubnetgroup',
defaultValue: 'lakhan-test',
description: 'cachesubnetgroup'
)

string (
name : 'maintenance_window',
defaultValue: 'mon:07:30-mon:08:30',
description: 'maintenance_window'
)

string (
name : 'elasticacheSecurityGroup',
defaultValue: 'sg-0c7781ad400565805,',
description: 'elasticacheSecurityGroup'
)
string (
name : 'cache_replica_per_nodegroup',
defaultValue: '1',
description: 'cache_replica_per_nodegroup'
)

  }




  stages {

    stage('CF Stack Opreation ') {
      steps {
          wrap([$class: 'BuildUser']) {
          sh '''#!/bin/bash -xe
          echo ${BUILD_USER}
          echo "Full name :  $BUILD_USER"
          CURRENT_DIRECTORY=`pwd`
          cd $CURRENT_DIRECTORY

          TEMPLATE_PATH=/var/jenkins_home/workspace/Test123/test.json

          PARAMETERS_PATH=parameters.json

          envsubst < ${PARAMETERS_PATH} > test_parameters.json

          cat test_parameters.json  


          #aws cloudformation create-stack --stack-name $STACK_NAME  --region $AWS_REGION  --template-body "file://"$TEMPLATE_PATH --parameters "file://test_parameters.json" --capabilities CAPABILITY_IAM --tags"Key"="Owner1" , "Key"="Owner","Value"="Enablement" "Key"="CreatedBy","Value"=${BUILD_USER} "Key"="Jenkins_Job","Value"="App-Services-elasticache-Setup"

asas
          if ! aws cloudformation describe-stacks --region $AWS_REGION --stack-name $STACK_NAME ; then

           aws cloudformation create-stack --stack-name $STACK_NAME  --region $AWS_REGION  --template-body "file://"$TEMPLATE_PATH --parameters "file://test_parameters.json" --capabilities CAPABILITY_IAM --tags "Key"="Owner1" ,"Key"="Owner","Value"="Enablement" "Key"="CreatedBy","Value"="${BUILD_USER}" "Key"="Jenkins_Job","Value"="App-Services-elasticache-Setup"

           aws cloudformation wait stack-create-complete --stack-name $STACK_NAME --region $AWS_REGION

         else

           aws cloudformation update-stack --stack-name $STACK_NAME  --region $AWS_REGION  --template-body "file://"$TEMPLATE_PATH --parameters "file://test_parameters.json" --capabilities CAPABILITY_IAM --tags "Key"="Owner1", "Key"="Owner","Value"="Enablement" "Key"="CreatedBy","Value"="${BUILD_USER}" "Key"="Jenkins_Job","Value"="App-Services-elasticache-Setup"

           aws cloudformation wait stack-update-complete --stack-name $STACK_NAME --region $AWS_REGION

         fi

          '''
      }
    }
  }
}
}
