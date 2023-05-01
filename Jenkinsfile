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
                    withCredentials([string(credentialsId: 'e39c6aee-4e98-4db1-9be4-37ce0520e5c5', variable: 'sohail')]) {
                        sh 'docker login -u sohail57865 -p ${sohail}'
                    }
                       sh 'docker tag images:2.0 sohail57865/nodejs:2.0'
                       sh 'docker push sohail57865/nodejs:2.0'
                       sh 'docker container run -d -p 3000:3000 images:2.0 npm run start'
                }
            }
        }
    }
}
                        sh 'docker login -u mirza57865 -p ${sohail}'
                    }
                       sh 'docker tag images:2.0 abbasmarolix/nodejs:2.0'
                       sh 'docker push abbasmarolix/nodejs:2.0'
                       sh 'docker container run -d -p 3000:3000 images:2.0 npm run start'
                }
            }
        }
    }
}
