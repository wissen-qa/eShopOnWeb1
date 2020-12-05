
pipeline {
  agent any
  stages {
    stage('SCM Checkout') {
      steps {
        sh "git clone https://github.com/uday-nitjsr/eShopOnWeb.git"
      }
    }
 stage('Docker Build') {
   steps {
     sh "docker-compose build"
     sh "docker-compose up -d"
      }
    }
  }
}
