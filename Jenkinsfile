pipeline {
    agent any

    stages {
        stage('Prepare Workspace') {
            steps {
                // Use shell commands to clean the workspace
                sh 'rm -rf *'
            }
        }

        stage('Checkout') {
            steps {
                // Cloning the repository with shell commands
                // Assuming you have set up credentials and the Git URL in the Jenkins environment
                sh 'git clone https://github.com/HUMBL3B33/mern-app-Deployment.git .'
            }
        }

        stage('Start Client') {
            steps {
                // Navigate to the client directory and start the client
                script {
                    sh '''
                    cd client/
                    npm start &
                    '''
                }
            }
        }

        stage('Start Server') {
            steps {
                // Navigate to the server directory and start the server
                script {
                    sh '''
                    cd server/
                    npm run dev &
                    '''
                }
            }
        }
    }

    post {
        always {
            // Output a simple completion message
            echo 'Pipeline execution complete.'
        }
    }
}
