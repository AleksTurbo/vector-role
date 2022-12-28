pipeline {
    agent {
        label 'linux'
    }
    stages {
        stage('Git') {
            steps{
                git branch: 'main', credentialsId: 'ff6f0a10-9ad2-41c5-b4d3-347b06b475c4', url: 'git@github.com:AleksTurbo/vector-role.git'
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
                sh 'pip3 install --user "molecule_docker" "ansible-lint<6.0.0" flake8'
                // sh 'pip3 install --user "molecule==3.6.1"'
                sh 'python3 -m pip install -U git+https://github.com/ansible-community/molecule'
                sh 'whoami'
                sh 'pwd'
                sh 'cat /etc/hostname'
                sh 'ls -la'
                }
        }
        stage('Check install') {
            steps{
                sh 'docker --version && ansible --version && molecule --version'
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