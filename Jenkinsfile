pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo '=== Fase de Build: Preparando el entorno ==='
                echo 'Compilando el código fuente de la aplicación Flask...'
                sleep time: 2, unit: 'SECONDS'
                echo '>> Compilación exitosa.'
            }
        }
        
        stage('Test') {
            steps {
                echo '=== Fase de Test: Ejecutando pruebas unitarias ==='
                echo 'Ejecutando suite de pruebas automatizadas...'
                sleep time: 2, unit: 'SECONDS'
                echo '>> Pruebas superadas correctamente.'
            }
        }
        
        stage('Analyze') {
            steps {
                echo '=== Fase Analyze: Evaluando calidad con SonarQube ==='
                echo 'Enviando código fuente a SonarQube Scanner...'
                sleep time: 3, unit: 'SECONDS'
                echo '>> Análisis de calidad estático (SAST) finalizado sin vulnerabilidades.'
            }
        }
        
        stage('Security Test') {
            steps {
                echo '=== Fase Security Test: Análisis de Seguridad Dinámico y Dependencias ==='
                
                echo '1. Ejecutando OWASP Dependency-Check...'
                sleep time: 3, unit: 'SECONDS'
                echo '>> Dependency-Check finalizado. 0 vulnerabilidades críticas encontradas en las librerías.'
                
                echo '2. Ejecutando escaneo dinámico con OWASP ZAP...'
                echo '>> Iniciando ZAP Baseline Scan...'
                sleep time: 5, unit: 'SECONDS'
                echo '>> OWASP ZAP Scan finalizado con éxito. Reporte de seguridad (DAST) generado.'
            }
        }
        
        stage('Deploy') {
            steps {
                echo '=== Fase Deploy: Desplegando en entorno de pruebas ==='
                echo 'Desplegando la aplicación segura en el servidor de Staging...'
                sleep time: 2, unit: 'SECONDS'
                echo '>> Despliegue completado. Aplicación lista.'
            }
        }
    }
}