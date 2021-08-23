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
            bat 'mvn clean install'
            app = docker.build("dewnisubasinghe/dewni-assignment1")
            docker.withRegistry( "https://registry.hub.docker.com", "dockerhub" ) {
              // dockerImage.push()
              app.push("latest")
            }
          }

        }

      }
    }

    stage('Orchestrate') {
      steps {
        script {
          sh 'kubectl apply -f demo.yaml'
        }

      }
    }

  }
}
