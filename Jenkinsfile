pipeline {
    agent any
    environment {
        AWS_DEFAULT_REGION="us-east-2"
    }
    stages {
        stage ('Git Checkout') {
          steps {
              git credentialsId: '5d51a221-75dc-47f8-a296-89af31ae45e3', url: 'https://github.com/zaval13/Terraform-AWS'
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
