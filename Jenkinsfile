pipeline {
    agent any
    environment {
        AWS_DEFAULT_REGION="us-east-2"
    }
    stages {
        stage ('Git Checkout') {
          steps {
              git credentialsId: '2d6bc20a-2088-4b87-ae94-ae51d3934d10', url: 'https://github.com/zaval13/Terraform-AWS'
          }
       }
        stage('Terraform Init') {
            steps {
                dir('./Terraform') { 
                  withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '50fe9061-584d-4471-88b1-ef1dc1275f4c', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                   sh 'terraform init'
              }
           }
         }      
        }
        stage('Terraform Apply') {
            steps {
              dir('./Terraform') {  
                withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '50fe9061-584d-4471-88b1-ef1dc1275f4c', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                  sh 'terraform apply --auto-approve'
              }
           }
         }      
       }
    }
}
