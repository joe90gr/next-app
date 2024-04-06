pipeline {
    agent none
    tools {nodejs "NODEJS"}

    stages {
        stage('Checkout') {
            agent { 
                label 'agent1'
            }
            steps {
                git branch: 'main', url: 'https://github.com/joe90gr/next-app'
            }
        }
        
        stage('Install dependencies') {
            agent { 
                label 'agent1'
            }
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            agent { 
                label 'agent1'
            }
            steps {
                parallel(
                    a: {
                        sh 'npm run build'
                    },
                    b: {
                        sh 'echo something elso'
                    }
                )
            }
        }

        stage('Test') {
            agent { 
                label 'agent1'
            }
            steps {
                sh 'npm run lint'
            }
        }

        stage('Deploy') {
            agent { 
                label 'agent1'
            }
            steps {
                sh 'echo deploy'
                // Deploy your application
                // This might involve copying built files to a server, or deploying to a cloud platform
                // Example:
                // sh 'npm run deploy'
            }
        }
    }

    // post {
    //     always {
    //         sh 'echo always'
    //         // Cleanup steps if necessary
    //         // Example:
    //         // sh 'npm ci'  // Use npm ci for clean install
    //     }
    // }
}
