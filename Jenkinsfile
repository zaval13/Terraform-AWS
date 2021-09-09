pipeline {
    agent any
    environment {
        AWS_DEFAULT_REGION="us-east-2"
    }
    stages {
        stage ('Git Checkout') {
          steps {
              git credentialsId: '630fba4e-fb03-4484-b58e-f37054e7215a', url: 'https://github.com/zaval13/Terraform-AWS'
          }
       }
        stage('Terraform Init') {
            steps {
                dir('./Terraform') { 
                  withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '22e826b2-22ef-49c7-88b1-89134644be0f', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                   sh 'terraform init'
              }
           }
         }      
        }
        stage('Terraform Apply') {
            steps {
              dir('./Terraform') {  
                withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '22e826b2-22ef-49c7-88b1-89134644be0f', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                  sh 'terraform apply --auto-approve'
              }
           }
         }      
       }
    }
}
