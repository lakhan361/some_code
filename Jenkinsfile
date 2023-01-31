pipeline {
    agent any

    environment {
        FOO = "bar"

    }

    stages {
        stage("Env Variables") {
            steps {
                echo "FOO = ${env.FOO}" // prints "FOO = bar"
                withEnv(["FOO=foobar"]) { // it can override any env variable
                    echo "FOO = ${env.FOO}" // prints "FOO = foobar"
                }

            }
        }

        }
    }

