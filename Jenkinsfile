pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
//   environment {
//     DOCKERHUB_CREDENTIALS = credentials('dockerhub')
//   }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t ajayperaboina/jenkins-docker-hub .'
      }
    }
    stage('Login & Push') {
      steps {
        sh 'echo "Peraboin@85" | docker login -u ajayperaboina --password-stdin'
        sh 'docker push ajayperaboina/jenkins-docker-hub'
      }
    }
    // stage('Deploy') {
    //   steps {
    //     sh 'kubectl apply -f deploy.yaml'
    //   }
    // }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}