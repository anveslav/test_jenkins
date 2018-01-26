node {
    stages {
        stage('cleaning') {
            steps {
                bat 'gradlew clean -x test'
            }
        }
        stage('building') {
            steps {
                bat 'gradlew build -g /cache/.gradle --info'
            }
        }
         stage('testing') {
                    steps {
                bat 'gradlew build -g /cache/.gradle --info'
            }
         }
    }
}