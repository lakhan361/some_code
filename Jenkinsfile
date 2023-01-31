pipeline {
    agent any

    parameters {
        string(
      name : 'AWS_REGION',
      defaultValue: 'us-east-1',
      description: 'AWS AccRegion'
    )
        string(
      name : 'S3_BUCKET_NAME',
      defaultValue: 'nextgen-lambda-packages',
      description: 'S3 Bucket for Code Package'
    )
    }

    stages {
        stage('CF Stack Opreation ') {


            steps {
                script {
                    def INPUT_PARAMS_ENV = input(
                            message: 'Please Select Environment',
                            ok: 'Next',
                            parameters: [
                              choice(
                                      name : 'ASP_ENV',
                                      choices: ['qa', 'stage', 'prod'],
                                      description: 'ASP_ENV example qa,stage or prod'
                                    ),

                                    choice(
                                    name: 'ENVIRONMENT',
                                    choices: ['travel-qa', 'travel-stage', 'travel-prod'],
                                    description: 'ENVIRONMENT'
                                  )

                                    ])

                    switch (env.ENVIRONMENT) {
                                      case 'travel-qa':
                            environment {
                                TAAS == 'master'
                            }

                            break
                                      case 'travel-stage':
                            environment {
                                TAAS == 'master'
                            }
                            break
                                      case 'travel-prod':
                            environment {
                                TAAS == 'master'
                            }
                    }

                    env.ASP_ENV = INPUT_PARAMS_ENV.ASP_ENV
                    env.ENVIRONMENT = INPUT_PARAMS_ENV.ENVIRONMENT
                }

                script {
                    echo "Update Card Operation ${ASP_ENV} ${ENVIRONMENT} ${TAAS}"
                }
            }
        }
    }
}
