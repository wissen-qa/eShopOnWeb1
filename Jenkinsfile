pipeline {
  agent any
  stages {
    stage('Docker Build') {
      steps {
        sh "sudo docker-compose build"
      }
    }
    stage('Docker Delete Old Containers') {
      steps {
        sh "sudo docker ps --filter 'label=name=Demo_App' -q | xargs --no-run-if-empty sudo docker container stop"
        sh "sudo docker ps --filter 'label=name=Demo_App' -q | xargs -r sudo docker container rm"
        }
      }
    }
    stage('Docker Compose Up') {
      steps {
        sh "sudo docker-compose up -d"
      }
    }
    stage('Apply Kubernetes Files') {
      steps {
          sh 'echo Kubernetes'
        }
      }
  }
}
post {
    success {
      slackSend(message: "Pipeline is successfully completed.")
    }
    failure {
      slackSend(message: "Pipeline failed. Please check the logs.")
    }
}
}
