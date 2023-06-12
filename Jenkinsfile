pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Build number is : ${env.BUILD_NUMBER}"
                sh "docker build -t httpd_dk:${env.BUILD_NUMBER} ."
                
                sh "docker run -it -d -p 8081:80 httpd_dk:${env.BUILD_NUMBER}"
               
            }
        }
        stage('Run') {
            steps {  
                sh "docker run -it -d -p 8081:80 httpd_dk:${env.BUILD_NUMBER}"               
            }
        }
    }
}
