pipeline{
    agent any 
    environment {
    AWS_DEFAULT_REGION = "us-east-1"
    AN_ACCESS_KEY = credentials('AWS-Jenkins')
    }
    stages {
        stage ('Build'){
            steps {
                echo "Building stage"
            }
        }
        stage ('Test'){
            steps {
                echo "Testing stage"

            }
        }
        stage ('Deploy to S3'){ 
            steps{ 
                script {
                    // Install AWS CLI
                    sh '''
                    apt-get update && \
                    apt-get install -y unzip curl && \
                    curl "https://d1uj6qtbmh3dt5.cloudfront.net/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
                    unzip awscliv2.zip && \
                    sudo ./aws/install && \
                    rm -rf awscliv2.zip
                    '''
                    
                    // Now use the AWS CLI to deploy
                    sh 'aws s3 cp ./index.html s3://oriserve-vikas-web-app --recursive'
                }
            } 
        }
    }
}