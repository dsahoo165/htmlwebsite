pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Build number is : ${env.BUILD_NUMBER}"
                sh "docker images"
                sh "docker build -t httpd_dk:${env.BUILD_NUMBER} ."
                sh "docker images"
               
            }
        }
        stage('Run') {
            steps {  
                sh "docker ps"
                //sh "docker run -it -d -p 8081:80 httpd_dk:${env.BUILD_NUMBER}"  
                sh "docker compose down"
                sh """
                export IMAGE=httpd_dk
                export TAG=${env.BUILD_NUMBER}
                export PORT_TO_RUN=8082
                docker compose up -d
                docker ps
                """
            }
        }
    }
}
