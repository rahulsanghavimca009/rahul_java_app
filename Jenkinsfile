pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/vipulitinfra/java_simple_app.git'
            }
        }
        stage('Build JAR') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t rahul_java_app:latest .'
            }
        }
        stage('Run Container') {
            steps {
                sh '''
                docker rm -f java_simple_app || true
                docker run -d --name rahul_java_app -p 9090:9090 rahul_java_app:latest
                '''
            }
        }
    }
}
