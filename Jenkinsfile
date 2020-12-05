pipeline {
  agent any
  stages {
    stage('Docker Build') {
      steps {
        sh "sudo docker-compose build"
      }
    }
    stage('Docker Push') {
      steps {
        sh "sudo docker ps --filter 'label=name=Demo_App' -q | xargs --no-run-if-empty sudo docker container stop"
        sh "sudo docker ps --filter 'label=name=Demo_App' -q | xargs -r sudo docker container rm"
        }
      }
    }
    stage('Docker Remove Image') {
      steps {
        sh "sudo docker-compose up -d"
      }
    }
    stage('Apply Kubernetes Files') {
      steps {
          withKubeConfig([credentialsId: 'kubeconfig']) {
          sh 'cat deployment.yaml | sed "s/{{BUILD_NUMBER}}/$BUILD_NUMBER/g" | kubectl apply -f -'
          sh 'kubectl apply -f service.yaml'
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
