pipeline {
  agent any
  stages {
    stage('Initialize') {
      steps {
        echo 'Initializing'
      }
    }

    stage('Test') {
      steps {
        echo 'Estoy haciendo tests'
        writeFile(file: 'ejemplo.txt', text: 'Escribiendo text')
      }
    }

    stage('Build') {
      steps {
        sh 'java --version'
      }
    }

    stage('Deploy') {
      steps {
        sh 'echo "haciendo deploy"'
        fileExists 'ejemplo.txt'
        echo 'terminando...'
      }
    }

  }
  post {
    always {
      junit(allowEmptyResults: true, testResults: '*/test-reports/.xml')
    }

  }
}