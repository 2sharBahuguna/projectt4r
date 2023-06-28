pipeline {

    agent any



    stages {

        stage('Authentication') {

            steps {

                sh '''
                
                    aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 854171615125.dkr.ecr.us-east-1.amazonaws.com

                    echo authenticating..

                '''

            }

        }



        stage('Build') {

            steps {

                
                

               sh '  
               
                    docker build -t tba-simple-flask .
                docker tag tba-simple-flask:latest 854171615125.dkr.ecr.us-east-1.amazonaws.com/tba-simple-flask:latest
                echo building...'

            }

        }



        stage('Push to ECR') {

            steps {

                

                sh 'echo pushing...

                    docker push 854171615125.dkr.ecr.us-east-1.amazonaws.com/tba-simple-flask:latest
                
                '

            }

        }

    }

}
stage('Build Yolo5 app') {
   steps {
       sh '''
           
       '''
   }
}
