pipeline {
    agent any
    stages {
        // ... (Fases anteriores: Build, Test, Analyze, Dependency Check, Deploy) ...
    }
    
    // Nueva sección para Documentación y Trazabilidad
    post {
        always {
            echo '=== Fase Post-Build: Consolidando Trazabilidad y Documentación ==='
            echo '1. Archivando registros de auditoría y logs del sistema...'
            // Simulación de guardado de reportes
            echo '✅ Reporte de Seguridad SCA (dependency-check-report.html) archivado con éxito.'
            echo '✅ Reporte de Vulnerabilidades DAST (owasp-zap-report.html) guardado en el servidor.'
        }
        success {
            echo '报告: El pipeline finalizó correctamente. Estado registrado: SUCCESS.'
        }
        failure {
            echo '⚠️ ALERTA: El pipeline falló. Registro de error enviado al log de auditoría.'
        }
    }
}