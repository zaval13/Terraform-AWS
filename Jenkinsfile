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
                  withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '0b7c251c-8a06-4207-bd66-f2ac525e25e6', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                   sh 'terraform init'
              }
           }
         }      
        }
        stage('Terraform Apply') {
            steps {
              dir('./Terraform') {  
                withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '0b7c251c-8a06-4207-bd66-f2ac525e25e6', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                  sh 'terraform apply --auto-approve'
              }
           }
         }      
       }
    }
}
