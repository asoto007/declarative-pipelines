pipeline{
    agent any
    
    environment{
        SENTENCE = "I hope your brother's El camino runs forever"
    }

    triggers{
        cron('0 3 * * 1-5')
    }
    
    stages{
        stage('SCM'){
            steps{
                git 'https://github.com/asoto007/declarative-pipelines.git'
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
                    return param.branch == "release"
                }
            }
            steps{
                echo 'Packing the code'
            }
        }
    }
}

                
