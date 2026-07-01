pipeline {
    agent any

    stages {
        stage('Build') {
            steps { echo 'Compilando...'; sleep 2 }
        }
        stage('Test') {
            steps { echo 'Pruebas unitarias...'; sleep 2 }
        }
        stage('Analyze') {
            steps { echo 'SonarQube...'; sleep 2 }
        }
        stage('Dependency Check') {
            steps {
                echo '=== Fase SCA: Analizando requirements.txt ==='
                script {
                    if (fileExists('requirements.txt')) {
                        def reqs = readFile('requirements.txt')
                        if (reqs.contains('1.1.4') || reqs.contains('2.11.3')) {
                            // Si detecta las versiones viejas, el pipeline FALLA a propósito
                            error('❌ ALERTA CRÍTICA: Dependencias vulnerables detectadas (Flask 1.1.4 / Jinja2 2.11.3). Actualice a versiones seguras.')
                        } else {
                            // Si detecta versiones nuevas, el pipeline PASA
                            echo '✅ Análisis SCA aprobado. Dependencias seguras.'
                        }
                    } else {
                        echo 'No se encontró requirements.txt.'
                    }
                }
            }
        }
        stage('Security Test') {
            steps { echo 'OWASP ZAP...'; sleep 2 }
        }
        stage('Deploy') {
            steps { echo 'Desplegando...'; sleep 2 }
        }
    }
}