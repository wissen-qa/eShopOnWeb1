node{
    stage('SCM Checkout'){
       git credentialsId: '02577ad1-6206-4d6f-8284-db061b89cac7', url: 'https://github.com/uday-nitjsr/eShopOnWeb.git'

    }
    
    stage('Build Docker Image'){
       cd 'home/BuildMachine/git_workspace/eShopOnWeb'
       sh 'docker-compose build '
       sh 'docker-compose up -d'
    }
}
