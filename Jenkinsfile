pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo '=== Fase de Build: Preparando el entorno ==='
                // Aquí irían los comandos para instalar dependencias de tu app (ej. pip install -r requirements.txt)
            }
        }
        
        stage('Test') {
            steps {
                echo '=== Fase de Test: Ejecutando pruebas unitarias ==='
                // Aquí irían los comandos de pruebas (ej. pytest)
            }
        }
        
        stage('Analyze') {
            steps {
                echo '=== Fase Analyze: Evaluando calidad con SonarQube ==='
                // Aquí Jenkins se conectaría con tu SonarQube Scanner
            }
        }
        
        stage('Security Test') {
            steps {
                echo '=== Fase Security Test: Análisis de Seguridad ==='
                
                echo '1. Ejecutando OWASP Dependency-Check...'
                // Aquí Jenkins buscaría vulnerabilidades en tus librerías
                
                echo '2. Ejecutando escaneo dinámico con OWASP ZAP...'
                // Este es el comando que reparamos en el Paso 5. 
                // IMPORTANTE: Cambia "http://IP_DE_TU_APP:5000" por la URL real de tu aplicación levantada.
                sh 'docker run --rm -t zaproxy/zap-stable zap-baseline.py -t http://localhost:8080'
            }
        }
        
        stage('Deploy') {
            steps {
                echo '=== Fase Deploy: Desplegando en entorno de pruebas ==='
                // Aquí iría el comando final para levantar tu aplicación segura
            }
        }
    }
}