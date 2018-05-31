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
    stage('get kernel') {
      steps {
        script {
          try {
            KERNEL_VERSION = sh (script: "uname -r", returnStdout: true)
          } catch(err) {
            echo "CAUGHT ERROR: ${err}"
            throw err
          }
        }

      }
    }
    stage('say kenel') {
      steps {
        echo '"${KERNEL_VERSION}"'
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