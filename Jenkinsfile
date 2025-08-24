pipeline {
    agent any
    
    stages {
        stage("one") {
            steps {
                echo 'step 1'
                sh 'mvn compile'
            }
        }
        stage("two") {
            steps {
                echo 'step 2'
                sh 'mvn clean test'
            }
        }
        stage("three") {
            steps {
                echo 'step 3'
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
