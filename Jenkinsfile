pipeline {
    agent {label 'jenkins-slave-2'}
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
                deploy adapters: [tomcat9(credentialsId: '74708006-4dd2-4eb5-b321-c83e5c9408e2', path: '', url: 'http://54.208.15.49:8080/')], contextPath: 'app', war: '*/*.war'
            }
            
        }
        stage("Deploy on Prod"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: '74708006-4dd2-4eb5-b321-c83e5c9408e2', path: '', url: 'http://54.208.15.49:8080/')], contextPath: 'app', war: '*/*.war'
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
