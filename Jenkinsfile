pipeline {
    agent any

    tools {
        terraform 'terraform'
    }
    stages {
        stage('Checkout from Git') {
            steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/awsactivators/Jenkins-Terraform-Deploy-Pipeline.git']]])            

          }
        }
        
        stage ("terraform init") {
            steps {
                sh 'terraform init' 
            }
        }

        stage ("terraform fmt") {
            steps {
                sh 'terraform fmt' 
            }
        }

        stage ("terraform validate") {
            steps {
                sh 'terraform validate' 
            }
        }

        stage ("terraform plan") {
            steps {
                sh 'terraform plan' 
            }
        }
        
        stage ("terraform apply") {
            steps {
                echo "Terraform action is --> ${apply}"
                sh 'terraform apply --auto-approve' 
           }
        }
    }
}
