pipeline {
    agent any
 
    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
            }
        }
 
        stage('Test') {
            steps {
                script {
                    echo 'Running tests...'
                    // Create test log file
                    sh 'echo "Test log - everything passed" > test.log'
                }
            }
        }
 
        stage('Security Scan') {
            steps {
                script {
                    echo 'Running security scan...'
                    // Create audit log file
                    sh 'echo "Security scan completed with 0 vulnerabilities." > audit.log'
                }
            }
        }
    }
 
    post {
        always {
            emailext (
                subject: "Jenkins Build #${env.BUILD_NUMBER} Result: ${currentBuild.currentResult}",
                body: "The pipeline has completed.\n\nBuild URL: ${env.BUILD_URL}",
                to: 'hgaur602@gmail.com',
                attachmentsPattern: '*.log',
                mimeType: 'text/plain'
            )
        }
    }
}
