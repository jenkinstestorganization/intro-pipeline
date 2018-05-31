pipeline {
  agent {
    label 'jdk9'
  }
  stages {
    stage('say hello') {
      steps {
        echo 'Hello World from Yogi'
        sh 'java -version'
      }
    }
  }
}