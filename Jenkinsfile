def branchIsDev = (env.BRANCH_NAME == 'dev')
def branchIsMaster = (env.BRANCH_NAME == 'master')

//def artifactsToArchive = 'app/build/outputs/apk/*'

// set job properties - storing 10 sets of artifacts for dev/master and 2 for other branches
//def artifactsToStore = 2
//if (branchIsDev || branchIsMaster) { artifactsToStore = 10 }
//properties([buildDiscarder(logRotator(artifactNumToKeepStr: "${artifactsToStore}")) ])


node('master') {

  // set environment variables
  env.PATH = "${tool 'gradle-4.0'}/bin:${tool 'Sonar_Scanner'}/bin:${env.PATH}"
  env.GRADLE_USER_HOME = env.WORKSPACE

  stage('Clear workspace') {
    sh 'rm -rf *'
    sh 'rm -rf .[^.] .??*'
  }
  
  stage('Git checkout') {
    checkout scm
  }
  
  try {

      stage('Gradle: Build') {
        sh '''
          gradle clean build -x test
        '''
      }

      stage('Gradle: Test') {
        sh '''
          gradle test
        '''
      }



    if (branchIsDev || branchIsMaster) {
      stage('SonarQube analysis') {
        withSonarQubeEnv('Sonar') {
          sh "sonar-scanner -Dsonar.projectVersion=$BUILD_NUMBER"
        }
      }
    }
    
  }
  catch(exception) {
  
    currentBuild.result = 'FAILURE'
    
  }
}
