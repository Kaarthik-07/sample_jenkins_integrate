pipeline {
    agent any

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-21-amazon-corretto'
        PATH = "/usr/lib/jvm/java-21-amazon-corretto/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'java -version'
                sh 'javac -version'
                sh 'mvn -version'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Install') {
            steps {
                sh 'mvn install'
            }
        }
    }

    post {
        success {
            echo 'Maven pipeline completed successfully.'
        }
        failure {
            echo 'Maven pipeline failed. Check the console output.'
        }
        always {
            echo 'Pipeline execution finished.'
        }
    }
}
