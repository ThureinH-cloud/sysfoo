pipeline {
  agent any
  stages {
    stage('one') {
      steps {
        echo 'compiling the app....'
        sh 'mvn compile'
      }
    }

    stage('two') {
      steps {
        echo 'testing the app....'
        sh 'mvn clean test'
      }
    }

    stage('three') {
      steps {
        echo 'packaging the app....'
        sh 'mvn package -DskipTests'
        sh 'mvn -v'
      }
    }

  }
  tools {
    maven 'Maven 3.9.11'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}