pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/joe90gr/next-app'
            }
        }
        
        stage('Install dependencies') {
            steps {
                // Install Node.js and npm
                sh 'curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -'
                sh 'sudo apt-get install -y nodejs'
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm run test'
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo deploy'
                // Deploy your application
                // This might involve copying built files to a server, or deploying to a cloud platform
                // Example:
                // sh 'npm run deploy'
            }
        }
    }

    post {
        always {
            sh 'echo always'
            // Cleanup steps if necessary
            // Example:
            // sh 'npm ci'  // Use npm ci for clean install
        }
    }
}
