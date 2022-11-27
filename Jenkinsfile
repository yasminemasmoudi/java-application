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
                    sh 'mvn test'
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
    }
}