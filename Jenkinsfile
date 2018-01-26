pipeline {
    agent any
    stages {
        stage('cleaning') {
            steps {
                sh 'gradle clean -x test'
            }
        }
        stage('building') {
            steps {
                sh 'gradle build -g /cache/.gradle --info'
            }
        }
         stage('testing') {
                    steps {
                sh 'gradle build -g /cache/.gradle --info'
            }
         }
    }
}