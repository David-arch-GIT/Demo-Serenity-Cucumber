pipeline {
    agent any

    environment {
        // Ruta de tu JDK 17 (según los logs de Maven)
        JAVA_HOME = 'C:\\Program Files\\Eclipse Adoptium\\jdk-17.0.17.10-hotspot'

        // Añadimos Java y Maven al PATH para este pipeline
        PATH = "${env.JAVA_HOME}\\bin;C:\\apache-maven-3.9.11\\bin;${env.PATH}"
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/David-arch-GIT/Demo-Serenity-Cucumber.git'
            }
        }

        stage('Build & Test') {
            steps {
                // Verificar que JAVA_HOME y Maven están bien
                bat 'echo JAVA_HOME=%JAVA_HOME%'
                bat 'java -version'
                bat 'mvn -version'

                // Ejecutar los tests de Serenity
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
