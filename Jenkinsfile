pipeline {
    agent any
    tools{
        maven 'Maven 3.9.11'
    }
    stages {
        stage("one") {
            steps {
                echo 'compiling the app....'
                sh 'mvn compile'
            }
        }
        stage("two") {
            steps {
                echo 'testing the app....'
                sh 'mvn clean test'
            }
        }
        stage("three") {
            steps {
                echo 'packaging the app....'
                sh 'mvn package -DskipTests'
            }
        }
    }

    post {
        always {
            echo 'This pipeline is completed..'
        }
    }
}
