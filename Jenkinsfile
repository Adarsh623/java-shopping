pipeline {
    agent any
    
    tools {
        maven 'Maven3'
        jdk 'jdk17'
    }
    
    stages {
        stage('Git Checkout') {
            steps {
                checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Adarsh623/java-shopping.git']])
            }
        }
        stage('create artifacts') {
            steps {
                sh 'mvn clean package -DskipTests=true'
            }
        }
        stage('build docker image') {
            steps {
                sh 'docker build -t shoppingcart:latest -f docker/Dockerfile .'
            }
        }
        stage('run docker image') {
            steps {
                sh 'docker run -d --name shoppingapp -p 8070:8070 shoppingcart:latest'
            }
        }
    }
}
