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
                
                withSonarQubeEnv(credentialsId: 'sonarqube-api-key') {
                // some block
                }  
            }
        }
    }
}

withSonarQubeEnv(credentialsId: 'sonarqube-api-key') {
    bat "mvn clean package sonar:sonar"
}