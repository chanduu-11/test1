pipeline {
    agent any
    tools
    {
        maven "Maven-3.9.12"
    }
    
    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/kavyarangaiah/test1.git'
            }
        }
        stage('Maven Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Docker Image') {
            steps {
                sh 'docker build -t rkavya/mavenwebapp .'
            }
        }
        stage('K8s Deployment') {
            steps {
                sh 'kubectl apply -f k8s-deploy.yml'
            }
        }
    }
}
