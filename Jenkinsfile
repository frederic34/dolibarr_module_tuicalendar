pipeline {
  agent any
  stages {
    stage('Prepare') {
      steps {
        sh 'composer install'
      }
    }
    stage('PHP Syntax check') {
      steps {
        sh 'vendor/bin/parallel-lint --exclude vendor/ .'
      }
    }
  }
}
