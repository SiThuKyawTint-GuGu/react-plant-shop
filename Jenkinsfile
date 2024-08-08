pipeline {
    agent {
        label 'agent-via-ssh'
    }
    environment {
        compose_service_name = 'react-jenkins-docker'
        workspace = '/home/guguskyer/project/react-jenkins-docker/'
    }
    stages {
        stage('Checkout Source') {
            steps {
                ws("${workspace}") {
                    checkout scm
                }
            }
        }
        stage('Docker Compose Build') {
            steps {
                ws("${workspace}") {
                    sh "docker compose build --no-cache ${compose_service_name}"
                }
            }
        }
        stage('Docker Compose Up') {
            steps {
                ws("${workspace}") {
                    sh "docker compose up --no-deps -d ${compose_service_name}"
                }
            }
        }
    }
}
