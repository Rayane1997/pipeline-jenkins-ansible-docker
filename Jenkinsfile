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
                sh "mvn -f greetings-app/pom.xml clean package"
            }           
        } 
        // Static Code Analysis (SonarQube)
        stage("Static Code Analysis (SonarQube)"){
            steps{
                echo "====++++  Static Code Analysis (SonarQube) ++++===="                
                sh "mvn -f greetings-app/pom.xml clean package -Dsurefire.skip=true sonar:sonar -Dsonar.host.url=http://172.17.0.1:9000   -Dsonar.projectName=challenge-09-ci-cd-jenkins-ansible -Dsonar.projectVersion=$BUILD_NUMBER";
             
            }           
        } 

    }
}