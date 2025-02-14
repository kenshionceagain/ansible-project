pipeline {
    agent any
    parameters {
        string(name: 'SERVER1', defaultValue: '10.0.1.10')
        string(name: 'SERVER2', defaultValue: '10.0.1.11')
    }
    stages {
        stage('Setup') {
            steps {
                script {
                    def inventory = """
                    [webservers]
                    ${params.SERVER1}

                    [dbservers]
                    ${params.SERVER2}
                    """
                    writeFile file: 'inventory.ini', text: inventory
                }
            }
        }
        stage('Deploy') {
            steps {
                ansiblePlaybook(
                    playbook: 'playbook-docker.yml',
                    inventory: 'inventory.ini'
                )
            }
        }
    }
}
