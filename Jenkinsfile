pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
            
                git 'https://github.com/David-arch-GIT/Demo-Serenity-Cucumber.git'
            }
        }

        stage('Build & Test') {
            steps {
                // Opcional, pero útil para validar Java y Maven
                bat 'java -version'
                bat 'mvn -version'

                // Ejecuta los tests de Serenity
                bat 'mvn clean verify'
            }
        }

        stage('Report') {
            steps {
                
                publishHTML([
                    reportDir: 'target/site/serenity',
                    reportFiles: 'index.html',
                    reportName: 'Serenity Report'
                ])
            }
        }
    }
}
