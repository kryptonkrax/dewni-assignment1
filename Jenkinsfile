pipeline {
agent any
    tools {
        maven 'Maven 3.3.9'
        jdk 'jdk8'
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }
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
