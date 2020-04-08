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
                echo 'building Completed through jenkinsfile'
            }
            

        }
    }
}