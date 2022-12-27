pipeline {
    agent {
        label 'linux'
    }
    stages {
        stage('Git') {
            steps{
                git branch: 'main', credentialsId: '9a34c925-16f7-41e7-9c21-a91b9a4b96d0', url: 'git@github.com:AleksTurbo/vector-role.git'
            }
        }
        stage('Test'){
            steps{
                echo 'Test message'
                sh 'whoami'
                sh 'pwd'
            }
        }
        stage('Soft install') {
            steps{
                sh 'pip3 install --user "molecule==3.6.1" "molecule_docker" "ansible-lint<6.0.0" flake8'
                sh 'whoami'
                sh 'pwd'
                sh 'ls -la'
                }
        }
        stage('Check install') {
            steps{
                sh 'docker --version && ansible --version && ansible-lint --version && molecule --version'
                sh 'pwd'
            }
        }
        stage('Molecule test'){
            steps{
                sh 'molecule test'
                cleanWs()
            }
        }
    }
}