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
                // echo "//<npm-registry>:8080/:_authToken=$AUTH_TOKEN" > ~/.npmrc
                sh 'npm-cli-login -u jenkins-user -p 12345 -e hectoralejandro2121@gmail.com -r http://192.168.0.7:8081/repository/backend/'
                 // echo "//192.168.0.5:8080/:_authToken=NpmToken.97519605-bd0c-3d21-ae38-e58420da0e27" > ~/.npmrc
                // sh 'npm config set email=hectoralejandro2121@gmail.com && npm config set _auth NpmToken.97519605-bd0c-3d21-ae38-e58420da0e27 && npm config set registry http://192.168.0.7:8081/repository/backend/ && npm config set always-auth=true && npm login --registry=http://192.168.0.7:8081/repository/backend/ && echo "jenkins-user" && echo "12345" && echo "hectoralejandro2121@gmail.com" && npm whoami && npm --registry=http://192.168.0.7:8081/repository/backend/ publish ./dist/app.js'
                // sh 'npm adduser<<! $USER_NEXUS 12345 hectoralejandro2121@gmail.com !'
                // sh 'npm config set email=hectoralejandro2121@gmail.com && npm config set _auth NpmToken.97519605-bd0c-3d21-ae38-e58420da0e27 && npm config set registry http://192.168.0.7:8081/repository/backend/ && npm config set always-auth=true && npm --registry=http://192.168.0.7:8081/repository/backend/ publish ./dist/app.js'
                sh 'npm config set email=hectoralejandro2121@gmail.com && npm config set _auth NpmToken.97519605-bd0c-3d21-ae38-e58420da0e27 && npm config set registry http://192.168.0.7:8081/repository/backend/ && npm config set always-auth=true && echo 192.168.0.7:8081/:_authToken=NpmToken.97519605-bd0c-3d21-ae38-e58420da0e27 ~/.npmrc && npm whoami --registry=http://192.168.0.7:8081/repository/backend/'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
