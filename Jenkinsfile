pipeline {

    agent any

    stages {

        stage('Setup Environment') {

            steps {
                bat 'call env.setup.bat'
            }
        }

        stage('Run Sanity Suite') {

            steps {
                bat 'npm run test:datadriven'
            }
        }

        stage('Generate Allure Report') {

            steps {
                allure([
                    includeProperties: false,
                    jdk: '',
                    results: [[path: 'allure-results']]
                ])
            }
        }
    }

    post {

        success {
            echo 'Automation executed successfully'
        }

        failure {
            echo 'Automation execution failed'
        }
    }
}