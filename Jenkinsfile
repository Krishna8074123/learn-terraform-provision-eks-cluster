pipeline {
agent any 
stages {
    stage('image build') {
        steps {
            sh 'terraform init'
        }
    }
    stage('image push') {
        steps {
            sh 'terraform apply --auto-approve'
        }
    }
    stage('image run') {
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