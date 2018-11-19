pipeline {
    agent any

stages{
        stage('Build'){
          steps {
          def mvn_version = 'maven'
          withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] ) {
            echo 'Now Archiving...'
            
          }

        }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
         stage('Deploy to Staging'){
            steps{
                build job: 'deploy-to-staging'
            }
         }
         stage('Deploy to Production'){
            steps{
                timeout(time:5, unit: 'DAYS'){
                    input message:'Approve PRODUCTION Deployment?'
                }
                build job: 'deploy-to-prod'
            }
            post{
                success {
                    echo 'Code Deployed to Production'
                }

                failure{
                    echo 'Deployment failed.'
                }
            }
         }
    }
}
