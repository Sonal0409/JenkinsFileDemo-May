pipeline{
    
    agent any  // here 'any' means run the pipeline on current server
    
    tools{
        maven 'mymaven'
    }
    
    stages{
        stage('Checkout Code'){
            
            steps{
                git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
            }
            
        }
        
        stage('Compile Code'){
            steps{
                sh 'mvn compile'
                sh 'mvn pmd:pmd'
            }
        }
        
         stage('Test Code'){
            steps{
                sh 'mvn test'
            }
            post{
                success{
                    junit stdioRetention: '', testResults: 'target/surefire-reports/*.xml'
                }
            }
        }
        
        stage('Build Code'){
            
            steps{
                sh 'mvn package'
            }
        }
        
    }
}
