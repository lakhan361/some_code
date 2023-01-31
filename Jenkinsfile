pipeline {
  agent any
    parameters {
    string (
      name : 'S3_BUCKET',
      defaultValue: 's3://test123456lakhan',
      description: 'Bucket_name.'
    )
    string (
      name : 'ROLE_ARN',
      defaultValue: 'arn:aws:iam::426765591064:role/bucket-policy-deletion-s3',
      description: 'Role for the task.'
    )
  }

    stage('CF Stack Opreation') {
      steps {
          timeout(time: 360, unit: 'SECONDS') {
          script {
          def INPUT_PARAMS = input(
                           message: 'Please Provide Parameters',
                           ok: 'Next',
                           parameters: [
                                  choice (
                                    name: 'ENVIRONMENT',
                                    choices: ["travel-qa", "travel-stage", "travel-prod"],
                                    description: 'ENVIRONMENT'
                                  ),


                          ])
                          switch(env.ENVIRONMENT) {
                                      case 'travel-qa':
                                        TaasCultureS3Bucket = master
                                        break
                                      case 'travel-stage':
                                        TaasCultureS3Bucket = 2020Q1
                                        break 
                                      case 'travel-prod':
                                        TaasCultureS3Bucket = 2019Q4
      
                          env.ENVIRONMENT = INPUT_PARAMS.ENVIRONMENT

                          env.TaasCultureS3Bucket = $TaasCultureS3Bucket
                         
                 sh '''#!/bin/bash -xe
                  echo $TaasCultureS3Bucket
          '''
 
            

      }
      }

    }
  }
}
}
