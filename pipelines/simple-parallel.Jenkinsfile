pipeline{
    agent any

    parameters{
        string(name: 'branch', defaultValue: 'master', description: 'Branch to fetch for the pipeline')
    }
    
    stages{
        stage('SCM'){
            steps{
                git branch: "${params.branch}", url: 'https://github.com/asoto007/declarative-pipelines.git'
            }
        }

        stage('static analysis'){
            steps{
                echo 'perform static analysis'
                sleep time: 3, unit: 'SECONDS'
            }
        }

        stage('build'){
            steps{
                echo 'Build the code'
                sleep time: 3, unit: 'SECONDS'
            }
        }

        stage('unit test'){
            steps{
                echo 'execute unit tests'
                sleep time: 3, unit: 'SECONDS'
            }
        }

        stage('Package'){
            when{
                expression{
                    return params.branch == "release"
                }
            }
            steps{
                echo 'Packing the code'
            }
        }
    }
}

                
