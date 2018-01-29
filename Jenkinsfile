node{
    checkout scm
        sh 'chmod +x gradlew'
      stage('cleaning') {
        sh './gradlew clean -x test'
    }
      stage('building') {
        sh './gradlew build -g /cache/.gradle --info'
              }
      stage('testing') {
        sh './gradlew -g /cache/.gradle test --info'
                }
}