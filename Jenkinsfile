pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }
        stage('install') {
            steps {
                bat 'mvn clean install'
            }
        }

        stage('gatling') {
            input {
                message "continue to gating"
            }
            steps {
                bat 'mvn gatling:test'
            }
            post {
                always {
                    gatlingArchive()
                }
            }
        }

        stage('message') {
            steps {
                bat 'echo finished'
            }
        }
    }
}