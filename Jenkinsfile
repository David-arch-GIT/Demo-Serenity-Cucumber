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
                // Útil para validar que Jenkins está usando bien Java y Maven
                bat 'java -version'
                bat 'mvn -version'

                // Ejecuta los tests de Serenity
                bat 'mvn clean verify'
            }
        }

        stage('Report') {
            steps {
                // Publica el reporte de Serenity en Jenkins
                publishHTML([
                    reportDir: 'target/site/serenity',
                    reportFiles: 'index.html',
                    reportName: 'Serenity Report'
                ])
            }
        }
    }
}
