pipeline {
    agent any

    stages {
        stage('Pull Source Code') {
            steps {
                git branch: 'master', url: 'git@github.com:navinkumar2701007/woodex.git'
            }
        }

        stage('Deploy to Nginx Server') {
            steps {
                sh "rsync -az --delete ./ ubuntu@15.207.221.194:/var/www/NAVIN/"
                sh "ssh ubuntu@15.207.221.194 'sudo systemctl restart nginx'"
            }
        }
    }

    post {
        success {
            echo "🚀 Deployment Successful!"
        }
        failure {
            echo "❌ Deployment Failed!"
        }
    }
}

