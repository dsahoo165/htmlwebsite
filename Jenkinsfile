pipeline {
    agent any

    stages {
        stage('Build Image') {
            steps {
                echo "Build number is : ${env.BUILD_NUMBER}"
                sh "docker images"
                script {
                      // Build the Docker image
                      docker.build("httpd_dk:${env.BUILD_NUMBER}")
                }
                //sh "docker build -t httpd_dk:${env.BUILD_NUMBER} ."
                sh "docker images"
               
            }
        }
        stage('Run Image') {
            steps {  
                sh "docker ps"
                //sh "docker run -it -d -p 8081:80 httpd_dk:${env.BUILD_NUMBER}"  
                sh "docker compose down"
                sh """
                export IMAGE=httpd_dk
                export TAG=${env.BUILD_NUMBER}
                export PORT_TO_RUN=8081
                docker compose up -d
                docker ps
                """
            }
        }
    }
}
