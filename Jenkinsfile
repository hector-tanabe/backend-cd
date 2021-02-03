pipeline {
    agent any
    triggers {
      pollSCM('0 */1 * * 1-5')
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'npm --version'
                sh 'npm run build'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
