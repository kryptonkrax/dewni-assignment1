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
        echo 'building phase'
      }
    }

  }
}