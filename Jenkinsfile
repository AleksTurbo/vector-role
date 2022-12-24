pipeline {
    agent {
        label 'linux'
    }
    stages {
        stage('Git') {
            steps{
                git branch: 'main', credentialsId: 'b072f0ea-e67f-4322-8b8c-1d7a044e293a', url: 'git@github.com:AleksTurbo/vector-role.git'
            }
        }
        stage('Test'){
            steps{
                echo 'Test steps'
            }
        }
        stage('Molecule install') {
            steps{
                sh 'pip3 install --user "molecule==3.4.0" "molecule_docker" "ansible-lint<6.0.0" flake8'
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