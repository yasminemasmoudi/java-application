pipeline{
    
    agent any 
    
    tools { 
        maven 'Maven 3.8.6' 
        jdk 'jdk11' 
    }
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
    }
}