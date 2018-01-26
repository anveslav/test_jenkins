pipeline {
    agent any
    stages {
        stage('cleaning') {
            steps {
                bat 'gradle clean -x test'
            }
        }
        stage('building') {
            steps {
                bat 'gradle build -g /cache/.gradle --info'
            }
        }
         stage('testing') {
                    steps {
                bat 'gradle build -g /cache/.gradle --info'
            }
         }
    }
}