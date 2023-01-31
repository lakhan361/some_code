pipeline {
    agent any

    environment {
        FOO = "bar"

    }

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
                switch (env.ENVIRONMENT) {
                        case 'travel-qa':
                            echo "FOO = ${env.FOO}" // prints "FOO = bar"
                            withEnv(["FOO=foobar"]) { // it can override any env variable
                            echo "FOO = ${env.FOO}" // prints "FOO = foobar"
                }
                }

            }
            }
        }

        }
    }
