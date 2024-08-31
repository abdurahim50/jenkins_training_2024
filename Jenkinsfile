pipeline {
    agent { label 'mybuild' }

    stages {
        stage('Checkout') {
            steps {
                // Clone the GitHub repository
                git url: 'https://github.com/abdurahim50/jenkins_training_2024.git'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    def targetDir = "/var/www/html"
                    // Deploy the static website to the local Apache server
                    sh """
                    sudo cp -r index.html ${targetDir}/
                    sudo chown www-data:www-data ${targetDir}/index.html
                    sudo chmod 644 ${targetDir}/index.html
                    """
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
