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
                // sh 'npm adduser --registry=http://192.168.0.7:8081/repository/npm-group/'
                // sh 'jenkins-user'
                // sh '12345'
                // sh 'hectoralejandro2121@gmail.com'
                // sh 'npm publish --registry http://192.168.0.7:8081/repository/npm-group/:_authToken=NpmToken.97519605-bd0c-3d21-ae38-e58420da0e27'
                sh 'npm install -g npm-cli-login
                sh 'npm config set email=hectoralejandro2121@gmail.com && npm config set _auth NpmToken.97519605-bd0c-3d21-ae38-e58420da0e27 && npm config set registry http://192.168.0.7:8081/repository/backend/ && npm config set always-auth=true && npm-cli-login -u jenkins-user -p 12345 -e hectoralejandro2121@gmail.com -r http://192.168.0.7:8081/repository/backend/ && npm --registry=http://192.168.0.7:8081/repository/backend/ publish ./dist/app.js'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
