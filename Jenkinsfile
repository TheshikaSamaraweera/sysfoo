pipeline {
    agent any

    tools {
        maven 'Maven 3.9.6'
               
    }

    stages {

        stage('build') {
            steps {
                echo "Running Maven Compile..."
                sh 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                echo "Running Maven Tests..."
                sh 'mvn clean test'
            }

        }

        stage('Package') {
            steps {
                echo "Packaging Application..."
                sh 'mvn package -DskipTests'
            }
            post {
                success {
                    archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline finished."
        }
    }
}
