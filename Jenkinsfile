pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Dockerize') {
      steps {
        sh 'docker build -t <image-name>:<tag> .'
        sh 'docker push <image-name>:<tag>'
      }
    }
    stage('Deploy') {
      steps {
        sh 'docker run -p 8080:8080 -d <image-name>:<tag>'
      }
    }
  }
}
