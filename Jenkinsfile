pipeline{

    agent any

    tools{
        maven 'LocalMaven'
    }

    stages{

        stage('Build'){
            steps{

                echo 'building project through jenkinsfile'
                sh 'mvn clean Package'
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