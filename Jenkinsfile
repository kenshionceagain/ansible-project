pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/kenshionceagain/ansible-project.git'
            }
        }

        stage('Execute Ansible Playbook') {
            steps {
                script {
                    // Assurez-vous qu'Ansible est installé sur l'agent Jenkins
                    sh 'ansible --version'

                    // Exécutez le playbook Ansible
                    sh 'ansible-playbook -i inventory playbook.yml'
                }
            }
        }
    }

    post {
        success {
            echo 'Le playbook Ansible a été exécuté avec succès.'
        }
        failure {
            echo 'L\'exécution du playbook Ansible a échoué.'
        }
    }
}
