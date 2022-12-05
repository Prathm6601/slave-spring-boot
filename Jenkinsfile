pipeline {
    agent "jenkins-slave-2"
     tools {
        maven 'MAVEN_HOME' 
        }
    stages {
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
                
            }
            
        }
        stage("Build"){
            steps{
                sh "mvn package"
                
            }
            
        }
        stage("Deploy on Test"){
            steps{
            // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'git-cred', path: '', url: 'http://54.84.49.65:8080/')], contextPath: 'slavef', war: '**/*.war'
            }
            
        }
        stage("Deploy on Prod"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'git-cred', path: '', url: 'http://54.84.49.65:8080/')], contextPath: 'slavef', war: '**/*.war'
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
