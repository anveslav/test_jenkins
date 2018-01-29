def branchIsDev = (env.BRANCH_NAME == 'dev')
def branchIsMaster = (env.BRANCH_NAME == 'master')


node('master') {

  stage('Git checkout') {
    checkout scm
  }

      stage('Gradle: Build') {
        bat './gradlew clean build -x test'
      }

      stage('Gradle: Test') {
        bat './gradle test'
      }

stage('Sonar checking'){
withSonarQubeEnv {

        bat './gradlew clean sonarqube'
    }
    }

}
