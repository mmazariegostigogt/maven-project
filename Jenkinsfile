pipeline {
    agent any

stages{
        stage('Build'){
                def mvn_version = 'M3'
            withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] ) {
            sh '''for f in i7j-*; do
                    (cd $f && mvn clean package -Dmaven.test.skip=true -Dadditionalparam=-Xdoclint:none  | tee ../jel-mvn-$f.log) &
                  done
                  wait'''
            }
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
    }
}
