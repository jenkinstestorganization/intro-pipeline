pipeline {
  agent {
    label 'jdk8'
  }
  stages {
    stage('say hello') {
      steps {
        echo "Hello World from ${MY_NAME}"
        sh 'java -version'
        echo "${TEST_USER_USR}"
        echo "${TEST_USER_PSW}"
        echo "Hello ${params.Name}!"
      }
    }
    stage('Checkpoint') {
      steps {
        checkpoint 'Checkpoint'
      }
    }
    stage('Testing') {
      failFast true
      parallel {
        stage('Java 8') {
          agent {
            label 'jdk8'
          }
          steps {
            sh 'java -version'
            sleep(time: 10, unit: 'SECONDS')
          }
        }
        stage('Java 9') {
          agent {
            label 'jdk9'
          }
          steps {
            sh 'java -version'
            sleep(time: 20, unit: 'SECONDS')
          }
        }
      }
    }
  }
  environment {
    MY_NAME = 'yogi rajala'
    TEST_USER = credentials('test-user')
  }
  parameters {
    string(name: 'Name', defaultValue: 'whoever you are', description: 'Who should I say hi to?')
  }
}