pipeline {
  agent any
  stages {
    stage('checking pom') {
      steps {
        fileExists 'pom.xml'
      }
    }

    stage('build') {
      steps {
        sh 'mvn compile test package'
      }
    }

  }
}