pipeline {
  agent any
  stages {
    stage('Initialize') {
      steps {
        echo 'Initializing'
        isUnix()
        fileExists 'ejemplo.txt'
      }
    }

    stage('Test') {
      steps {
        echo 'Estoy haciendo tests'
        writeFile(file: 'ejemplo.txt', text: 'Escribiendo text')
        input(message: 'Aprobación Necesaria', id: '1')
      }
    }

    stage('Build') {
      steps {
        sh 'java --version'
      }
    }

    stage('Deploy') {
      parallel {
        stage('Deploy') {
          steps {
            sh 'echo "haciendo deploy"'
            fileExists 'ejemplo.txt'
            echo 'terminando...'
            writeFile(file: 'ejemplo.txt', text: 'haciendo el deploy')
          }
        }

        stage('error') {
          steps {
            echo 'Terminando Deploy'
          }
        }

      }
    }

  }
  post {
    always {
      junit(allowEmptyResults: true, testResults: '*/test-reports/.xml')
    }

  }
}