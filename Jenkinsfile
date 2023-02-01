pipeline { 
    agent any 
    stages { 
        stage('CF Stack Opreation ') { 

            environment { 
                CLOUDFRONT_ID = "test", 
                LAMBDA_SECURITY_GROUPS = "test", 
                TAAS_CULTURE_S3BUCKET = "test", 
                ORXE_CULTURE_S3BUCKET = "null" 
            } 
            steps { 
                script { 
                    def INPUT_PARAMS_ENV = input( 
                            message: 'Please Select Environment', 
                            ok: 'Next', 
                            parameters: [ 
                              choice( 
                                    name: 'ENVIRONMENT', 
                                    choices: ["travel-qa", "travel-stage", "travel-prod"], 
                                    description: 'ENVIRONMENT' 
                                    )]) 

                    env.ENVIRONMENT = INPUT_PARAMS_ENV 
                    if (env.ENVIRONMENT == 'travel-qa') 
                     { 
                        echo "hello world${env.ASP_ENV}" 
                        withEnv(["CLOUDFRONT_ID=EVAXRM1VVZ1KW", "LAMBDA_SECURITY_GROUPS=sg-0b359f227f7c95168", "TAAS_CULTURE_S3BUCKET=nextgen-translation-service-qa","ORXE_CULTURE_S3BUCKET=orxe-taas-culture-qa"]){ 
                        echo "${env.CLOUDFRONT_ID}  ${env.LAMBDA_SECURITY_GROUPS} ${env.TAAS_CULTURE_S3BUCKET} ${env.ORXE_CULTURE_S3BUCKET}" 
                        } 
                    } 

                    if (env.ENVIRONMENT == 'travel-stage') 
                     { 
                        echo "hello world${env.ASP_ENV}" 
                        withEnv(["CLOUDFRONT_ID=EX08MEKJHBTBJ", "LAMBDA_SECURITY_GROUPS=sg-0c3132d15c2fe16aa", "TAAS_CULTURE_S3BUCKET=nextgen-translation-service-stage","ORXE_CULTURE_S3BUCKET=orxe-taas-culture-stage"]){ 
                        echo "${env.CLOUDFRONT_ID}  ${env.LAMBDA_SECURITY_GROUPS} ${env.TAAS_CULTURE_S3BUCKET} ${env.ORXE_CULTURE_S3BUCKET}" 
                        } 

                    } 

                    if (env.ENVIRONMENT == 'travel-prod') 
                     { 
                        echo "hello world${env.ASP_ENV}" 
                        withEnv(["CLOUDFRONT_ID=E1J9FOQMD3689N", "LAMBDA_SECURITY_GROUPS=sg-0ddd5b934bf42cbcc", "TAAS_CULTURE_S3BUCKET=nextgen-translation-service","ORXE_CULTURE_S3BUCKET=orxe-taas-culture"]){ 
                        echo "${env.CLOUDFRONT_ID}  ${env.LAMBDA_SECURITY_GROUPS} ${env.TAAS_CULTURE_S3BUCKET} ${env.ORXE_CULTURE_S3BUCKET}" 
                        } 
                    } 

                 else 
                     { 
                        echo 'no values are passed' 
                     } 
                } 
      }}}} 
