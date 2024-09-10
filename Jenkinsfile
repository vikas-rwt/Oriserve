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
                withAWS(region: 'us-east-1', credentials: '') {
                    sh 'ls -la'
                    sh 'aws s3 cp ./index.html s3://oriserve-vikas-web-app --recursive'
                }
            } 
        }
    }
}