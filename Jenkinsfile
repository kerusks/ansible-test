pipeline {
    environment {
        PATH = "/user/local/bin:$PATH"
    }
    agent any
    
    tools {nodejs "node1"}
    stages {
        stage('GIT checkout') {
            steps {
                git 'https://github.com/kerusks/ansible-test.git'
            }
        }
        stage('Install') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        
        stage('Ansible execute') {
            steps {
                ansiblePlaybook installation: 'ansible', playbook: 'node.yml'
            }
        }        
    }
}