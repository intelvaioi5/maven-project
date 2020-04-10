pipeline{

    agent any
    parameters{
        
        string(name:'tomcat_dev',defaultValue:'\\localhost', description:'Staging Server')
        string(name:'tomcat_prod',defaultValue:'\\localhost',description:'Production server')
        string(name:'pkg_path',defaultValue:'C:\Program Files (x86)\Jenkins\workspace\FullyAutomated\webapp\target\webapp.war',description:'Package path')
    }

    tools{

        maven 'LocalMaven'
        jdk 'LocalJDK'
    }

    triggers{

        pollSCM('* * * * *')
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
        stage('Deployment Parallel'){
            parallel{

                stage('Deploy to Staging'){
                    steps{
                        echo 'Staging Deployment started'
                        sh cp '{params.pkg_path}' '{params.tomcat_dev}:d$\Tushar\Study\Tomcat 8.5\webapps'
                        echo 'Staging Deployment completed'
                    }

                }
                stage('Deploy to Production'){
                    steps{
                        echo 'Prod deployment started'
                        sh cp '{params.pkg_path}' '{params.tomcat_prod}:d$\Tushar\Study\Tomcat 8.5\webapps'
                        echo 'Prod deployment completed'
                    }
                }
            }
        }
        
    }
}