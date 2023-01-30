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
  
  
            def INPUT_PARAMS = input(
                           message: 'Please Provide Parameters',
                           ok: 'Next',
                           parameters: [
                                  choice (
                                    name: 'ENVIRONMENT',
                                    choices: ["travel-qa", "travel-stage", "travel-prod"],
                                    description: 'ENVIRONMENT'
                                  ),
                                  if ($ENVIRONMENT == "trav" 
                                  string (
                                    name : 'TaasCultureS3Bucket',
                                    description: 'Please provide bucket name where published file needs to be stored for taas flow',
                                    defaultValue: 'nextgen-translation-service-qa'
                                  ),
                                   string (
                                    name : 'OrxeCultureS3Bucket',
                                    description: 'Please provide bucket name where published file needs to be stored for orxe flow',
                                    defaultValue: 'orxe-taas-culture-qa'
                                  )
                          ])
  stages {
    stage('CF Stack Opreation ') {
      steps {
          sh '''#!/bin/bash -xe
          CURRENT_DIRECTORY=`pwd`
          cd $CURRENT_DIRECTORY
          echo "lakhan is here"


          '''
      }
    }
  }
}
