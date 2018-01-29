node{
    checkout scm
      stage('cleaning') {
        bat './gradlew clean -x test'
    }
      stage('building') {
        bat './gradlew build -g /cache/.gradle --info'
              }
      stage('testing') {
        bat './gradlew -g /cache/.gradle test --info'
                }
}