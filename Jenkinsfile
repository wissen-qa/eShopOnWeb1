pipeline {
  agent any
  stages {
    stage('Docker Build') {
      steps {
        sh "sudo docker-compose build"
      }
    }
    stage('Docker delete existing containers') {
      steps {
        sh "sudo docker ps --filter 'label=name=Demo_App' -q | xargs --no-run-if-empty sudo docker container stop"
        sh "sudo docker ps --filter 'label=name=Demo_App' -q | xargs -r sudo docker container rm"
      }
    }
     stage('Docker containers up') {
      steps {
        sh "sudo docker-compose up -d"
      }
    }
    stage('Docker Push') {
      steps {
        echo "docker push"
        }
      }
    }
    stage('Docker Remove Image') {
      steps {
        echo "docker remove"
      }
    }
    stage('Apply Kubernetes Files') {
      steps {
          echo "kubernetes"
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
