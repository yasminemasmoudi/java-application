pipeline{
    
    agent any 
    stages {
        
        stage('Git Checkout'){
            
            steps{
                
                script{
                    
                    git branch: 'main', url: 'https://github.com/yasminemasmoudi/java-application'
                }
            }
        }  
        stage('UNIT testing'){
            
            steps{
                
                script{
                    bat 'mvn test'
                }
            }
        } 

        stage('Integration testing'){
            
            steps{
                
                script{
                    
                    bat 'mvn verify -DskipUnitTests'
                }
            }
        }
        stage('Maven build'){
            
            steps{
                
                script{
                    
                    bat 'mvn clean install'
                }
            }
        }
        stage('Static code analysis'){
            
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonarqube-api-key') {
                    bat "mvn clean package sonar:sonar"
                    }
                }       
            }
        }
        stage('Quality Gate status'){
            
            steps{
                script{
                    waitForQualityGate abortPipeline: false, credentialsId: 'sonarqube-api-key' {
                    }
                }       
            }
        }
    }
}

