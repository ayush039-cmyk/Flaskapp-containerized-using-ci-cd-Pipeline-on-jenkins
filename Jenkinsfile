pipeline {
  agent any 
     environment {
         IMAGE_NAME = "dockerayush039/j-img"
        }
     stages{
      stage('Setup'){
         steps{
             sh "pip install --break-system-packages -r requirements.txt"
          }
        }
      stage('Log in to docker'){
          steps {
             withCredentials([
                usernamePassword(credentialsId:'docker-creds', usernameVariable:'USERNAME' , passwordVariable: 'PASSWORD')]) {
                sh "echo ${PASSWORD} | docker login -u ${USERNAME} --password-stdin" }
                echo 'Login Successful'
              }
            } 
       stage('Build image'){
          steps{
             sh '''docker build -t ${IMAGE_NAME} .'''             
             echo 'Docker image built successfully'
             sh 'docker image ls'
            }
           }
       stage('Push Image'){
          steps {
             sh "docker push ${IMAGE_NAME}"
             echo "pushed successfully"
           }
       }
   }
}                                 
