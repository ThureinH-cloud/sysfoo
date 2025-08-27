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
      parallel {
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

        stage('Docker B & P') {
          steps {
            script {
              docker.withRegistry('https://index.docker.io/v1/', 'dockerlogin') {
                def commitHash = env.GIT_COMMIT.take(7)
                def dockerImage = docker.build("thureinhtet2222/sysfoo:${commitHash}", "./")
                dockerImage.push()
                dockerImage.push("latest")
                dockerImage.push("dev")
              }
            }

          }
        }

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