pipeline{
    agent any


    environment {
        AWS_REGION = 'us-east-1'
        ECR_REGISTRY_URL = '854171615125.dkr.ecr.us-east-1.amazonaws.com'
        DOCKER_IMAGE_NAME = 'tb22-docker-image'
        DOCKER_IMAGE_TAG = '0.1.0'



    stages{
        stage('Build'){
            steps{
                sh 'echo "Hello World" '
                sh '''
                    echo "Multiline shell script works too"
                    ls -lah
                '''
            }
        }
        
        stage('Build Yolo5 app'){
            steps{

            sh '''

                aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 854171615125.dkr.ecr.us-east-1.amazonaws.com
                docker build -t tushar-yolo5 .
                docker tag tushar-yolo5:latest 854171615125.dkr.ecr.us-east-1.amazonaws.com/tushar-yolo5:latest
                docker push 854171615125.dkr.ecr.us-east-1.amazonaws.com/tushar-yolo5:latest
                '''
            }
        }
        stage('Trigger Deploy'){
            steps{
                build job: 'Yolo5Deploy', wait: false, parameters:[
                    string(name: 'YOLO5_IMAGE_URL', value: "854171615125.dkr.ecr.us-east-1.amazonaws.com/tushar-yolo5:latest")]
            }
        }
    }
}
