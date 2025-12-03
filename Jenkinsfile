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
                sh './hello.sh'
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

