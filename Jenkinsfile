pipeline {
    agent { label 'remote-label' }

    tools {
        maven "maven-3.6.2"
    }

    stages {
        stage('Build') {
            steps {
              
                //git branch: 'main', url: 'https://github.com/qf-clinic/my-app.git'
                 checkout scm
              
                sh "mvn -Dmaven.test.failure.ignore=true clean package"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }

            post {
             
                success {
                  
                    archiveArtifacts 'target/*.war'
                }
            }
        }
    }
}
