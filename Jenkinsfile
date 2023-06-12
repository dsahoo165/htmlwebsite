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
                sh "docker run -it -d -p 8081:80 httpd_dk:${env.BUILD_NUMBER}"  
                sh "docker ps"
            }
        }
    }
}
