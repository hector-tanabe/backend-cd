pipeline {
    agent any
    triggers {
      pollSCM('0 */1 * * 1-5')
    }
    
    environment {
        NEXUS_REGISTRY_URL = 'http://192.168.0.7:8081/repository/backend/'
        NEXUS_AUTH_TOKEN   = '12345'
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
        stage('Publish') {
            steps {
                echo 'Publishing...'
                sh 'npm publish'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
