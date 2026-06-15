pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: ' https://github.com/brundhas26/seleniumpractice.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
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
            echo 'Login Successful'
            echo 'Expected Inventory Page: https://www.saucedemo.com/inventory.html'
        }

        failure {
            echo 'Build FAILED'
        }
    }
}
