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
      name : 'PRIVATE_SUBNET_GROUP_ONE',
      description: 'DATA PRIVATE SUBNET_GROUP_ID'
      )
      string (
      name : 'PRIVATE_SUBNET_GROUP_TWO',
      description: 'DATA PRIVATE SUBNET_GROUP_ID'
    )
    string (
      name : 'PRIVATE_SUBNET_GROUP_THREE',
      description: 'DATA PRIVATE SUBNET_GROUP_ID'
    )
    string (
      name : 'INSTANCE_TYPE',
      defaultValue: 'kafka.m5.xlarge',
      description: 'INSTANCE_TYPE'
    )
    string (
      name : 'SECURITY_GROUP',
      description: 'SECURITY_GROUP'
    )
    string (
      name : 'CLUSTER_NAME',
      defaultValue: 'app-service-kafka',
      description: 'CLUSTER_NAME'
    )
    string (
      name : 'CLUSTER_VERSION',
      defaultValue: '2.6.1',
      description: 'CLUSTER_VERSION'
    )
    string (
      name : 'PURPOSE',
      defaultValue: 'business',
      description: 'PURPOSE'
    )
    string (
      name : 'KMS_KEY_ARN',
      description: 'KMS_KEY_ARN'
    )
    string (
      name : 'VOLUME_SIZE',
      defaultValue: "100",
      description: 'PRODUCT_OWNER'
    )
    string(
      description: 'Kafka Configuration ARN'
      name: 'CONFIGURATION_ARN',
    )
    string(
      name: 'AWS_REGION',
      description: 'AWS_REGION',
      defaultValue: 'us-east-1'
    )
    string(
      name: 'LOG_GROUP_NAME',
      description: 'LOG_GROUP_NAME',
      defaultValue: 'AppServices-kafka-log'
    )
    string(
      name: 'LOG_RETENTION',
      description: 'LOG_RETENTION in days Possible values are: 1, 3, 5, 7, 14, 30, 60, 90, 120, 150, 180, 365, 400, 545, 731, 1827, and 3653.',
      defaultValue: '7'
    )
    string(
      name: 'NO_BROKER_NODES',
      description: 'NO_BROKER_NODES',
      defaultValue: '3'
    )
    string(
      name: 'CF_STACK_NAME',
      description: 'Cloudformation Stack Name',
      defaultValue: 'App-Services-kafka-stack'
    )
  }
  stages {
    stage('CF Stack Opreation ') {
      steps {
          sh '''#!/bin/bash -xe
          CURRENT_DIRECTORY=`pwd`
          cd $CURRENT_DIRECTORY
          ls
          cat parameters.json
          echo $INSTANCE_TYPE
          '''
      }
    }
  }
}
