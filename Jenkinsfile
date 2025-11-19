pipeline {
    agent any

    stages {

        // Jenkins ya hace el "Declarative: Checkout SCM" solo,
        // usando tu repo David-arch-GIT/Demo-Serenity-Cucumber.
        // No hace falta otro git aquí.

        stage('Build & Test') {
            steps {
                // Opcional: ver qué Java y Maven ve Jenkins
                bat 'java -version'
                bat 'mvn -version'

                // Ejecutar pruebas de Serenity
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
