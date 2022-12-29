pipeline {
agent any 
    stages {
        stage('build') {
            steps {
                sh 'terraform init'
            }
        }
        stage('apply') {
            steps {
                sh 'terraform apply --auto-approve'
            }
        }
        stage('terraform run') {
            steps {
                sh 'aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name)'
            }
        }
        stage ('kubectl') {
            steps {
                sh 'kubectl apply -f deploy.yml'
            }
        }
        stage ('kubectl pods') {
            steps {
                sh 'kubectl get po'
            }
        }
    }
}
