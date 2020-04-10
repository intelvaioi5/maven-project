pipeline{

    agent any
    parameters{
        
        string(name:'tomcat dev',defaultValue:localhost, description:'Staging Server')
        string(name:'tomcat prod',defaultValue:localhost,description:'Production server')

    }

    tools{

        maven 'LocalMaven'
        jdk 'LocalJDK'
    }

    triggers{

        pollscm('* * * * *')
    }

    stages{

        stage('Build projecct'){
            steps{

                sh 'mvn clean package'
            }
            post{

                success{
                    echo 'Now Archieving'
                    archiveArtifacts artifacts:'**/target/*.war'
                }
            }

        }
    /*    stage('Deployment Parallel'){
            parallel{

                stage('Deploy to Staging'){

                }
            }
        }
        */
    }
}