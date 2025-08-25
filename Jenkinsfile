pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Mjsentiment/DevOpsClassCodes.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Install Jenkins via Ansible') {
            steps {
                sh 'ansible-playbook -i playbooks/inventory playbooks/jenkins.yml'
            }
        }

        stage('Install Docker via Ansible') {
            steps {
                sh 'ansible-playbook -i playbooks/inventory playbooks/docker.yml'
            }
        }

        stage('Deploy App via Ansible') {
            steps {
                sh 'ansible-playbook -i playbooks/inventory playbooks/app-deploy.yml'
            }
        }
    }
}
