pipeline {

    agent any

    ECR_URL = "854171615125.dkr.ecr.us-east-1.amazonaws.com"
    REPO_NAME="tushar-yolo5"



    stages {

        stage('Authentication') {

            steps {

                sh '''
                
                    aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 854171615125.dkr.ecr.us-east-1.amazonaws.com

                    

                '''

            }

        }



        stage('Build') {

            steps {

                
                

               sh '''  
                cd yolo5
            
                docker build -t tushar-yolo5 .
               '''

            }

        }



        stage('Push to ECR') {

            steps {

                

                sh '''
`                   docker tag tushar-yolo5:latest 854171615125.dkr.ecr.us-east-1.amazonaws.com/tushar-yolo5:latest
                    docker push 854171615125.dkr.ecr.us-east-1.amazonaws.com/tushar-yolo5:latest
                
                '''

            }

        }

    }
}
