pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Tshar007/jenkins-app.git',
                    credentialsId: 'github-id'
            }
        }
        stage('Build') {
            steps {
                echo "Running build from GitHub repo"
                // Execute hello.sh and print output
                sh(script: './hello.sh', returnStdout: false)
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'hello.sh', allowEmptyArchive: true
            }
        }
    }
    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}

