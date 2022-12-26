pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t techjd/dp-alpine:latest .'
      }
    }
    stage('Login') {
      steps {
      
        withCredentials([string(credentialsId: 'dockerId', variable: 'docker_password')])
        sh 'docker login -u techjd -p $dockerId'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push techjd/dp-alpine:latest'
      }
    }
  }
  
  post {
    always {
      sh 'docker logout'
    }
  }
}

