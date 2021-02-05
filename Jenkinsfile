pipeline {
    agent any
    triggers {
      pollSCM('0 */1 * * 1-5')
    }
    
    environment {
        NEXUS_REGISTRY_URL = 'http://192.168.0.7:8081/repository/backend/'
        NEXUS_AUTH_TOKEN   = 'amVua2lucy11c2VyOjEyMzQ1'
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
                /*withCredentials([usernamePassword(credentialsId: 'jenkins-user', usernameVariable: 'jenkins-user', passwordVariable: '12345')]) {
                nexusArtifactUploader(
                    nexusVersion: 'nexus3',
                    protocol: 'https',
                    nexusUrl: '192.168.0.7:8081',
                    version: tagG,
                    repository: 'backend',
                    credentialsId: 'jenkins-user',
                    artifacts: [
                        [artifactId: './dist/app.js',
                        type:'js',
                        classifier: '',
                        file: "myArchive-${tagG}.js"]
                        ]
                    )
                }*/
                sh 'npm publish --registry http://192.168.0.7:8081/repository/backend/_auth=amVua2lucy11c2VyOjEyMzQ1'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
