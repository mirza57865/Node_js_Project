pipeline{
    agent any
    stages{
        stage('checkout code'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/mirza57865/Node_js_Project']])
            }
        }
        stage('Build docker image'){
            steps{
             script{
                 sh 'docker build -t images:2.0 .'
             }   
            }
        }
        stage('create docker container'){
            steps{
                script{
                    withCredentials([file(credentialsId: '', variable: 'dockerhub')]) {
                        sh 'docker login -u abbasmarolix -p ${dockerhub}'
                    }
                       sh 'docker tag images:2.0 sohail57865/nodejs:2.0'
                       sh 'docker push sohail57865/nodejs:2.0'
                       sh 'docker container run -d -p 3000:3000 images:2.0 npm run start'
                }
            }
        }
    }
}
