pipeline{

    agent any

    tools{
        maven 'LocalMaven'
    }

    stages{

        stage('Build'){
            withMaven(maven : 'LocalMaven') {
                bat'mvn clean compile'
                echo 'building Completed through jenkinsfile'
            }
            post{

                success{
                    echo 'Now Archieving..'
                    archiveArtifact artifacts: '**/*.war'
                }
            }

        }
    }
}