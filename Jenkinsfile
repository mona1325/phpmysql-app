node{

    stage('SCM Checkout')
    {
        git credentialsId: '415be7d1-73fa-4313-a0b6-4b9d9021c592', url: 'https://github.com/mona1325/phpmysql-app.git'
    }
    
    stage('Run Docker Compose File')
    {
        sh 'docker-compose build'
        sh 'docker-compose up -d'
    }
    stage('PUSH image to Docker Hub')
    {
        withCredentials([string(credentialsId: 'DockerHubPassword', variable: 'DHPWD')]) 
        {
            sh "docker login -u vardhanns -p ${DHPWD}"
        }
        sh 'docker push vardhanns/phpmysql_app'
    }
}
