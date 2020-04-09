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
        }        
    }
}