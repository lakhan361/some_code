pipeline {
    agent any

    stages {
        stage("Env Variables") {
            steps {
                script {

                def INPUT_PARAMS = input(
                           message: 'Please Provide Parameters',
                           ok: 'Next',
                           parameters: [
                                  choice(
                                    name: 'ENVIRONMENT',
                                    choices: ['travel-qa', 'travel-stage', 'travel-prod'],
                                    description: 'ENVIRONMENT'
                                  )
                          ])
                }
                script {
                    ENVIRONMENT = $ENVIRONMENT
                
            }
                sh 'current value $ENVIRONMENT ${env.ENVIRONMENT}'
        }
        }
    }
}
