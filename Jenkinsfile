pipeline{

    agent any

    tools{
        maven 'LocalMaven'
    }

    stages{

        stage('Build'){
            steps{

                echo 'building project through jenkinsfile'
                sh 'mvn clean package'
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