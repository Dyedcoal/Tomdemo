pipeline{
    
    agent any 
    
    stages {
        
        stage('Git Checkout'){
            
            steps{ 
                    git 'https://github.com/Dyedcoal/Tomdemo.git'   
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
        stage('Static code analysis'){
            
            steps{
                
                script{
                    
                    withSonarQubeEnv(credentialsId: 'Sonar-auth') {
                        
                        sh 'mvn clean package sonar:sonar'
                    }
                   }
                    
                }
            }
            stage('Quality Gate Status'){
                
                steps{
                    
                    script{
                        
                        waitForQualityGate abortPipeline: false, credentialsId: 'Sonar-auth'
                    }
                }
            }
    }
        
}
