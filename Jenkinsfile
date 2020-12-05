
pipeline {
  agent any
  stage('Docker Build') {
   steps {
     sh "docker-compose build"
     sh "docker-compose up -d"
      }
    }
  }
}
