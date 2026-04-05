pipeline {
   agent any 
   environment {
      IMAGE_NAME = "saloni24gupta"
      VERSION = "v1.$${BUILD_NUMBER}"
      }
      
      stages {
          
          stage('clone codde') {
             steps {
                  git 'https://github.com/saloni24gupta/jenkins-demo.git'
             }
      }
      stage('build docker image') {
      steps {
      sh "docker build -t $IMAGE_NAME:$VERSION ."
      }
      }
      stage('Test') {
      steps {
       sh 'echo "Running basic test..."'
       sh 'cat index.html'
      }
}
stage('Push to Docker Hub') {
            steps {
                sh "docker push $IMAGE_NAME:$VERSION"
            }
        }
         stage('Deploy Container') {
            steps {
                sh "docker stop my-container || true"
                sh "docker rm my-container || true"
                sh "docker run -d -p 8086:80 --name my-container $IMAGE_NAME:$VERSION"
            }
        }      
}
