pipeline {
 agent any
     triggers {
            pollSCM 'H/10 * * * *'
        }
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
                bat 'gradlew -g /cache/.gradle test --info'
            }
         }
         stage('sonar checking') {
                              steps {
                        bat './gradlew sonarqube \
                              -Dsonar.host.url=http://localhost:9000 \
                              -Dsonar.login=880c690495dfd10da6f6cc0420801b3102cecfec'
                      }
                    }
    }
}