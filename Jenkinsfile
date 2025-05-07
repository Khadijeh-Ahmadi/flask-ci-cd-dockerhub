pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub-creds')
  }
  stages {
    stage('Cloner le dépôt') {
      steps {
        echo 'Clonage du dépôt terminé.'
      }
    }
    stage('Build de l\'image Docker') {
      steps {
        script {
          docker.build("${DOCKERHUB_CREDENTIALS_USR}/flask-ci-cd-dockerhub")
        }
      }
    }
    stage('Push vers DockerHub') {
      steps {
        script {
          docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-creds') {
            docker.image("${DOCKERHUB_CREDENTIALS_USR}/flask-ci-cd-dockerhub").push()
          }
        }
      }
    }
  }
}
