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
    stage('Check Debug') {
      steps {
        sh 'vendor/bin/var-dump-check --extensions php --tracy --exclude vendor/ .'
      }
    }
    stage('Checkstyle') {
      steps {
        sh 'vendor/bin/phpcs --standard=codesniffer/ruleset.xml --extensions=php --ignore=autoload.php --ignore=vendor/ .'
      }
    }
  }
}
