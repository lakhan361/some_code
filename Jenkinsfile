pipeline {
    agent any
    stages {
        stage('Hello') {
            steps {
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
                                  if ($ENVIRONMENT == "trav") {

                                    
                                  }
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
                    if (env.BRANCH_NAME == 'main') {
                        echo 'Hello from main branch'
                    }  else {
                        sh "echo 'Hello from ${env.BRANCH_NAME} branch!'"
                    }
                    }
              

            }
        }
    }
}
