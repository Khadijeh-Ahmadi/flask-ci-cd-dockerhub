pipeline {
  agent any

  stages {
    stage('Clone') {
      steps {
        echo ' Clonage du dépôt terminé.'
      }
    }

    stage('Build Docker Image') {
      steps {
        script {
          docker.build("khadijehahmadi/flask-ci-cd-test")
        }
      }
    }
    stage('Push to DockerHub') {
      steps {
        script {
          docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-creds') {
           docker.image("khadijehahmadi/flask-ci-cd-test").push()
         }
       }
     }
    }
  }
}

