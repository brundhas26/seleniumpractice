pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/brundhas26/newselenium.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Run Selenium') {
            steps {
                sh 'mvn exec:java -Dexec.mainClass=com.example.App'
            }
        }
    }

    post {
        success {
            echo 'Selenium Test Executed Successfully'
        }

        failure {
            echo 'Build Failed'
        }

        always {
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
        }
    }
}
