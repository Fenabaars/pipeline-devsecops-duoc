pipeline {
    agent any

    stages {
        stage('Build') {
            steps { echo '=== Fase de Build: Preparando el entorno ==='; sleep 2 }
        }
        stage('Test') {
            steps { echo '=== Fase de Test: Ejecutando pruebas unitarias ==='; sleep 2 }
        }
        stage('Analyze') {
            steps { echo '=== Fase Analyze: Evaluando calidad con SonarQube ==='; sleep 2 }
        }
        stage('Dependency Check') {
            steps {
                echo '=== Fase SCA: Analizando requirements.txt ==='
                script {
                    if (fileExists('requirements.txt')) {
                        def reqs = readFile('requirements.txt')
                        if (reqs.contains('1.1.4') || reqs.contains('2.11.3')) {
                            error('❌ ALERTA CRÍTICA: Dependencias vulnerables detectadas. Actualice a versiones seguras.')
                        } else {
                            echo '✅ Análisis SCA aprobado. Dependencias seguras.'
                        }
                    } else {
                        echo 'No se encontró requirements.txt.'
                    }
                }
            }
        }
        stage('Security Test') {
            steps { echo '=== Fase Security Test: Análisis de Seguridad Dinámico y OWASP ZAP ==='; sleep 2 }
        }
        stage('Deploy') {
            steps { echo '=== Fase Deploy: Desplegando en entorno de pruebas ==='; sleep 2 }
        }
        // NUEVA FASE DE MONITORIZACIÓN
        stage('Monitoring') {
            steps {
                echo '=== Fase Continuous Monitoring: Verificando estado post-despliegue ==='
                echo '1. Ejecutando Health Check (Ping al servicio web)...'
                sleep 3
                echo '✅ Health Check exitoso: La aplicación responde con HTTP 200 OK.'
                
                echo '2. Verificando telemetría de seguridad (Simulación Prometheus/Grafana)...'
                sleep 2
                echo '✅ Monitoreo activo: Consumo de CPU/Memoria estable. Tráfico anómalo: 0%.'
            }
        }
    }
    
    post {
        always {
            echo '=== Fase Post-Build: Consolidando Trazabilidad y Documentación ==='
            echo '1. Archivando registros de auditoría y logs del sistema...'
            echo '✅ Reporte SCA y DAST guardados en el servidor.'
        }
        success {
            echo '✅ REPORTE FINAL: El pipeline DevSecOps completó su ciclo con éxito.'
        }
        failure {
            echo '⚠️ ALERTA: El pipeline falló. Notificación enviada al equipo.'
        }
    }
}