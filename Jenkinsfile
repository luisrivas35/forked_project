pipeline {
  agent any
  stages {
    stage('Initialize') {
      steps {
        echo 'Esta es el inicio'
      }
    }

    stage('Test') {
      steps {
        sh 'mvn clean verify'
      }
    }

  }
  post {
    always {
      junit(allowEmptyResults: true, testResults: '*/test-reports/.xml')
    }

  }
}