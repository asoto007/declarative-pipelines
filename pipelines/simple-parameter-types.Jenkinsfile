pipeline{
    agent any
    parameters{
        text(name: 'multiline', defaultValue: 'This is a default multiline value for the parameter')

        booleanParam(name: 'isAdmin', defaultValue: false, description: 'Whether or not the current user is an admin')

        choice(name: 'targetEnvironment', choices:['dev', 'staging', 'qa', 'production'], description: 'Select the target environment')
    }

    stages{
        stage('List Parameters'){
            steps{
                steps{

                    echo "Text: ${params.multiline}"
                    echo "Is the current user admin?: ${params.isAdmin} 'Yes' : 'No'"
                    echo "Target Environment: ${params.targetEnvironment}"
                }
            }
        }
    }
}