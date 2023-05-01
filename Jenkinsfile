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
                 sh 'docker build -t images:2.1 .'
             }   
            }
        }
        stage('create docker container'){
            steps{
                script{
                    withCredentials([string(credentialsId: 'dockerhub', variable: 'dockerhub')]) {
                        sh 'docker login -u abbasmarolix -p ${dockerhub}'
                    }
                       sh 'docker tag images:2.1 abbasmarolix/nodejs:2.1'
                       sh 'docker push abbasmarolix/nodejs:2.1'
                       sh 'docker container run -d -p 3000:3000 images:2.1 npm run start'
                }
            }
        }
    }
}
