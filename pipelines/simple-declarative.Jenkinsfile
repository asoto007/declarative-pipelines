pipeline{
    agent any

    parameters{
        string(name: 'branch', defaultValue: 'master', description: 'Branch to fetch for the pipeline')
    }
    
    environment{
        SENTENCE = "I hope your brother's El camino runs forever"
    }

    triggers{
        cron('0 3 * * 1-5')
    }
    
    stages{
        stage('SCM'){
            steps{
                git branch: "${params.branch}", url: 'https://github.com/asoto007/declarative-pipelines.git'
            }
        }
        stage('HELLO'){
            steps{
                echo 'Hello world!'
                script{
                    def words = env.SENTENCE.split(' ')
                    for (word in words){
                        echo word
                    }
                }            
            }
        }

        stage('build'){
            steps{
                echo 'Build the code'
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

                
