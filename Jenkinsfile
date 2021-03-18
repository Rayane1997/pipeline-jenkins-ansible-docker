pipeline {
    agent any
    
    tools  {
        maven "my-maven"
    }

    stages {

        // Clone from Git
        stage("Clone App from Git"){
            steps{
                echo "====++++  Clone App from Git ++++===="
                git branch:"master", url: "https://github.com/Rayane1997/pipeline-jenkins-ansible-docker.git"
            }          
        }
        // Build and Unit Test (Maven/JUnit)
        stage("Build and Package"){
            steps{
                echo "====++++  Build and Unit Test (Maven/JUnit) ++++===="
                sh "mvn -f greetings-app/ clean package"
            }           
        }  

    }
}