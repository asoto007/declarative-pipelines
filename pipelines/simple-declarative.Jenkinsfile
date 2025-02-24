pipeline{
    agent any
    
    environment{
        SENTENCE = "I hope your brother's El camino runs forever"
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
    }
}

                
