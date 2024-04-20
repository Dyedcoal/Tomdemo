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
                    sh 'mvn test'   
            }
        }
        stage('Integration testing'){
            
            steps{ 
                    sh 'mvn verify -DskipunitTests'   
            }
        }
        stage('Maven Build'){
            
            steps{ 
                    sh 'mvn clean install'   
            }
        }
        stage('Static Code Analysis'){
            
            steps{
                scripts{
                     withSonarQubeEnv(credentialsId: 'Sonar-auth') {
                        sh 'mvn clean package sonar:sonar'
                    }

                }
               
                  
            }
        }
    }
        
}
