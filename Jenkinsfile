pipeline {
    agent any

    environment {
        // JDK 17 instalado en la máquina donde corre Jenkins
        JAVA_HOME = 'C:/Program Files/Eclipse Adoptium/jdk-17.0.17.10-hotspot'
        // Añadimos Java y Maven al PATH
        PATH = "${env.JAVA_HOME}/bin;C:/apache-maven-3.9.11/bin;${env.PATH}"
    }

    stages {

        stage('Checkout') {
            steps {
                // Clona tu propio repo
                git branch: 'master', url: 'https://github.com/David-arch-GIT/Demo-Serenity-Cucumber.git'
            }
        }

        stage('Build & Test') {
            steps {
                // Comprobar JAVA_HOME y Maven
                bat 'echo JAVA_HOME=%JAVA_HOME%'
                bat 'java -version'
                bat 'mvn -version'

                // Ejecutar tests de Serenity
                bat 'mvn clean verify'
            }
        }

        stage('Report') {
            steps {
                // Publicar el reporte de Serenity en Jenkins
                // (necesitas el plugin "HTML Publisher" instalado)
                publishHTML(target: [
                    reportDir: 'target/site/serenity',
                    reportFiles: 'index.html',
                    reportName: 'Serenity Report',
                    allowMissing: false,
                    alwaysLinkToLastBuild: true,
                    keepAll: true
                ])
            }
        }
    }
}
