pipeline {
    agent any
  
    environment {
        AWS_ACCESS_KEY_ID     = credentials('aws-access-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-access-key')
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'master', url: 'https://github.com/your-username/your-repo.git'
            }
        }
        stage('Run Terraform') {
            steps {
                bat 'terraform init'
                bat 'terraform plan'
                // User confirmation for applying changes (optional)
                input {
                    message 'Apply Terraform changes?'
                    options {
                        yes 'Yes'
                        no 'No'
                    }
                }
                bat 'terraform apply'
            }
        }
    }
}
