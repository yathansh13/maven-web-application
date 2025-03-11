pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/yathansh13/maven-web-application.git'
        BRANCH = 'master'
    }

    stages {
        stage('Clone Repository') {
            steps {
                echo "Cloning Repository from ${GIT_REPO}"
                git branch: "${BRANCH}", url: "${GIT_REPO}"
            }
        }

        stage('Build') {
            steps {
                echo "Building the Maven Project..."
                sh 'mvn clean package'
            }
        }
    }

    post {
        success {
            echo 'Build Successful'
        }
        failure {
            echo 'Build Failed'
            mail to: 'ys560@snu.edu.in',
                 subject: 'Jenkins Build Failed',
                 body: 'Check Jenkins for details'
        }
        always {
            echo 'Cleaning up workspace...'
            cleanWs()
        }
    }
}
