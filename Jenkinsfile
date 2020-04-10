pipeline{

    agent any

    tools{
        maven 'LocalMaven'
        jdk 'LocalJDK'
    }
    stages{

        stage('Build'){
            steps{

                echo 'building project through jenkinsfile'
                sh 'mvn clean package'
                echo 'building Completed through jenkinsfile'
            }
           post {
               success{
                   echo 'now archieving...'
                   archiveArtifacts artifacts: '**/target/*.war'
               }
           }

        }
        
        stage('Deploy to Staging'){
            steps{
                build job:'Deploy to Staging'
                echo 'deployment done on echo'
            }
            post{
                success{
                    echo 'Deploy to staging completed'
                }
                failure{
                    echo 'Staging Deployment failed'
                }
            }
        }

        stage('Deploy to Production'){

            steps{
                timeout(time:5, unit:'DAYS'){
                    input messge:'Approve Production Deployment?'
                }
                build job: 'Deploy to Prod'
            }
            post{
                success{
                    echo 'Deployed to Production completed'
                }
                failure{
                    echo 'Production Deployment failed'
                }
            }
        }
    }
}