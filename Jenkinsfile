pipeline{

    agent any

    tools{
        maven 'LocalMaven'
    }

    stages{

        stage('Build'){
            steps{

                echo 'building project through jenkinsfile'
                sh 'maven clean package'
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