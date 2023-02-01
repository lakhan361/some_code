pipeline {
    agent any



stages {
    stage("S3 Package Push") {

      steps {
        script {
          deploy()
        }
      }
    }
    stage('CF Stack Opreation ') {
      steps {
          script{
              def INPUT_PARAMS_ENV = input(
                            message: 'Please Select Environment',
                            ok: 'Next',
                            parameters: [
                              choice (
                                      name : 'ASP_ENV',
                                      choices: ['qa','stage','prod'],
                                      description: 'ASP_ENV example qa,stage or prod'
                                    )])
                  env.ASP_ENV = INPUT_PARAMS_ENV
            }
          script{
           
          echo "Verify Card Operation "${ASP_ENV}""
          }
      }}}}
