pipeline {
    agent any
    stages {
        stage('cleaning') {
            steps {
                sh 'gradlew clean -x test'
            }
        }
        stage('building') {
            steps {
                sh 'gradlew build -g /cache/.gradle --info'
            }
        }
         stage('testing') {
                    steps {
                sh 'gradlew build -g /cache/.gradle --info'
            }
         }
    }
}