pipeline {
  agent any
  stages {
    stage('Checking pom') {
      steps {
        fileExists 'pom.xml'
      }
    }

    stage('Build') {
      steps {
        dir(path: 'app') {
          script {
            git 'https://github.com/kryptonkrax/dewni-assignment1.git'
            sh 'mvn clean install'
            app = docker.build("dewnisubasinghe/dewni-assignment1")
            //docker.withRegistry( "", "dewnisubasinghe" ) {
              // dockerImage.push()
              app.push("latest")
            }

          }

        }
      }

      stage('Orchestrate') {
        steps {
          script {
            sh 'kubectl apply -f docker-k8s-demp.yaml'
          }

        }
      }

    }
    tools {
      jdk 'JAVA 8'
    }
  }