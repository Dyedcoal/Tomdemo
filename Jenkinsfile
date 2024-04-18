pipeline{
    
    agent any 
    
    stages {
        
        stage('Git Checkout'){
            
            steps{ 
                    git 'https://github.com/Tomiphred/Tomdemo.git'   
            }
        }
        stage('UNIT testing'){
            
            steps{ 
                withMaven{
                    sh "mvn test"
                }
            }
        }
    }
        
}
