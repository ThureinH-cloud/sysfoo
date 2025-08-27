pipeline {
  agent none
  stages {
    stage('one') {
      agent {
        docker {
          image 'maven:3.9.6-eclipse-temurin-17'
        }

      }
      steps {
        echo 'compiling the app....'
        sh 'mvn compile'
      }
    }

    stage('two') {
      agent {
        docker {
          image 'maven:3.9.6-eclipse-temurin-17'
        }

      }
      steps {
        echo 'testing the app....'
        sh 'mvn clean test'
      }
    }

    stage('three') {
      agent {
        docker {
          image 'maven:3.9.6-eclipse-temurin-17'
        }

      }
      steps {
        echo 'packaging the app....'
        sh 'mvn package -DskipTests'
        sh 'mvn -v'
        archiveArtifacts '**/target/*.jar'
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