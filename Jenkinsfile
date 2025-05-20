pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
    }

    post {
        always {
            emailext(
                subject: "Build ${currentBuild.fullDisplayName}",
                body: """
                Build result: ${currentBuild.currentResult}
                Commit message: ${env.GIT_COMMIT_MESSAGE}
                Commit author: ${env.GIT_COMMIT_AUTHOR}
                """,
                recipientProviders: [[$class: 'DevelopersRecipientProvider']],
                to: 'hgaur602@gmail.com'
            )
        }
    }
}
