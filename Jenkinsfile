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
                sh 'terraform destroy --auto-approve'
            }
        }
    }
}
