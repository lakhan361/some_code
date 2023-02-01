pipeline {
    agent any

    stages {
        stage('CF Stack Opreation ') {
            environment {
                USER_ID = 'null'
            }
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
                                    )])
                    env.ASP_ENV = INPUT_PARAMS_ENV
                    if (env.ASP_ENV == 'stage') {
                        echo "hello world${env.ASP_ENV}"
                        env.USER_ID = 'lark'
                        withEnv(["USER_ID=lark"]){
                        echo "${env.USER_ID}"
                        }


                    }
                 else
                     {
                        echo 'no'
                     }
                }
      }}}}
