pipeline{
    agent any
    stages{
        stage('List Environment Variables'){
            steps{
                script{
                    echo "Listing all Jenkins built-in environment variables"
                }
                sh '''
                echo "Environment variables:"
                echo "-----------------------"
                # Iterate through all the environment variables
                printenv | sort
                '''
            }
        }
    }
}