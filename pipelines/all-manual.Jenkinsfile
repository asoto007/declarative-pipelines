pipeline{
    agent any

    stages{
        stage('static-analysis'){
            steps{
                echo 'static-analysis'
                script{
                    input message: "Have you performed static analysis and that has resulted in no high or critical issues?"
                        ok: "Yes, I have"
                }
            }
        }
        stage('build'){
            steps{
                echo 'build'
            }
        }
        stage('unit test'){
            steps{
                echo 'unit test'
            }
        }
        stage('package'){
            steps{
                echo 'package'
            }
        }
    }
}