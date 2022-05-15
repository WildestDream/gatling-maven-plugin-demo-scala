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
            //可选执行
            input {
                message "continue to gating performance test"
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