pipeline {
  agent any
  stages {
    stage('tool versions') {
      parallel {
        stage('tool versions') {
          steps {
            sh '''java -version
git --version
'''
          }
        }

        stage('checking pom') {
          steps {
            fileExists 'pom.xml'
          }
        }

      }
    }

    stage('build') {
      steps {
        sh 'mvn clean install'
      }
    }

  }
}