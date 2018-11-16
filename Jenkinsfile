pipeline {
    agent any

stages{
        stage('Build'){
            steps {
                sh 'export M2_HOME=/users/vm_marco/DevOps/apache-maven-3.5.0'
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
