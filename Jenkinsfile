pipeline {
  agent any
  stages {
    stage('Docker Build') {
      steps {
        sh "docker-compose build"
        sh "docker-compose up -d"
      }
    }
  }
}
