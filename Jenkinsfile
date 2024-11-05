pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from your version control system
                git url:'https://github.com/adithya17122000/Jenkins', branch:'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Upgrade pip and install dependencies globally
                    bat '''
                    pip install --upgrade pip
                    '''
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Run tests using unittest
                    bat 'python -m unittest discover -s tests'
                }
            }
        }
    }

    post {
        always {
            // Clean up the workspace after the build
            cleanWs()
        }
        success {
            echo 'Tests passed successfully!'
        }
        failure {
            echo 'Tests failed!'
        }
    }
}
