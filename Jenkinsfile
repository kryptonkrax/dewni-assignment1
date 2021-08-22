pipeline {
  agent any
  stages {
    stage('checking pom') {
      steps {
        fileExists 'pom.xml'
      }
    }

    stage('tools') {
      steps {
        sh 'java -version'
      }
    }

  }
}