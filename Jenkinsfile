pipeline {
    agent any

stages{
        stage('Build'){
            steps {
                sh 'export M2_HOME=/opt/apache-maven-3.3.9'
                sh 'export PATH=$PATH:$M2_HOME/bin'
                sh 'mvn --version'
                sh 'mvn clean package'
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
