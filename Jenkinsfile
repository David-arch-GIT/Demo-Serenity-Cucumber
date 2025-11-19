pipeline {
    agent any

    // Si tienes JDK y Maven configurados como "Global Tools" en Jenkins,
    // pon aquí sus nombres. Si no sabes, puedes dejar comentado esto.
    tools {
        // jdk 'JDK17'       // Nombre de la JDK en Manage Jenkins > Global Tool Configuration
        // maven 'Maven3'    // Nombre de Maven si lo tienes configurado como tool
    }

    stages {

        // NO hacemos más git aquí, Jenkins ya hace el "Declarative: Checkout SCM"
        // usando tu repo (el que tiene el Jenkinsfile y tu pom.xml nuevo)

        stage('Build & Test') {
            steps {
                // Opcional, pero útil para verificar que usa la versión correcta de Java y Maven
                bat 'java -version'
                bat 'mvn -version'

                // Ejecuta los tests de Serenity (Failsafe + Serenity Maven Plugin)
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
