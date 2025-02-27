pipeline{
    agent any
    environment{
        ARTIFACT_SOURCE_DIRECTORY = "tests/*.xml"
        ORG = 'org'
        PROJECT = 'PROJECT'
        PIPELINE = 'PIPELINE'
        PAT = credentials('ado-pat')
    }

    stages{
        stage('Build'){
            steps{
                echo 'Build the code'
            }
        }
        stage('Test'){
            steps{
                echo 'Execute unit test'
                sh 'mkdir -p tests && echo "test results" >tests/testresults.xml'
                error "Broken tests break the build"
            }
        }
    }

    post{
        always{
            archiveArtifacts artifacts: ARTIFACT_SOURCE_DIRECTORY, followSymlinks: false

            echo 'upload the artifact to azure storage'

            scripts{
                //POST POST https://dev.azure.com/{organization}/{project}/_apis/build/builds?api-version=7.1

                def targetURL = "POST https://dev.azure.com/${env.ORG}/${env.PROJECT}/_apis/build/builds?definitionId=${env.PIPELINE_ID}&api-version=7.1"

                def authValue = ":${env.PAT}".bytes.encodeBase64().toString()

                sh "curl -X POST --header 'Content-Type: application/json' --header 'Content-Lenght: 0' --header 'Authorization: Basic ${env.PAT}' --url ${targetURL}"
            }
        }
    }
}
