## **Análisis de riesgos**
Explica la importancia de evaluar riesgos incluso en pequeñas empresas. Se detallan las fases:
- Conocer la situación actual: nivel de madurez, aspectos técnicos, organizativos y normativos
- Limitar el alcance: identificar activos críticos y priorizar controles
- Fases del análisis:
    - Identificación de activos
    - Cálculo de riesgo intrínseco
    - Probabilidad de ocurrencia
    - Riesgos no aceptables
    - Riesgo residual
- Mitigación del riesgo:
    - Implementar controles
    - Eliminar el riesgo
    - Transferirlo (p.ej., ciberseguros)
- El análisis debe ser continuo y medible, usando indicadores
## **Principios de la economía circular**
Se expone la necesidad de pasar del modelo lineal a uno circular en la industria 4.0:
- Convertir residuos en recursos
- Reutilizar, reparar y reciclar productos
- Aprovechamiento energético
- Sustituir combustibles fósiles
- Rediseñar procesos productivos para reducir impacto ambiental
- En TI se busca evitar la obsolescencia programada y fomentar productos sostenibles
## **Medidas técnicas de seguridad**
Se dividen en:
### Preventivas
- Antivirus/antimalware
- EDR/XDR
- Firewalls
- Copias de seguridad
- DLP
- Verificación de integridad
- VPNs y comunicaciones seguras
- IDS
- Virtual patching
- SIEM
### Reactivas
- Funciones de respuesta en EDR/XDR
- IPS (IDS con capacidad de acción)
- Planes de contingencia
- Verificación de integridad reactiva
- Virtual patching reactivo
## **Políticas de securización**
Diferencia entre:
- Política: obligatoria
- Buena práctica: recomendada
### Políticas organizativas:
- Continuidad de negocio
- Cumplimiento legal (RGPD, LOPDGDD)
- Relación con proveedores
- Concienciación y formación
- Uso del correo y dispositivos corporativos
- Uso de contraseñas
- Protección del puesto de trabajo
### Políticas técnicas:
- Auditorías
- Antimalware
- Control de acceso
- Copias de seguridad
- Gestión de logs
- Respuesta a incidentes
- Actualizaciones
- Borrado seguro
- Teletrabajo
## **Guías de buenas prácticas**
No son obligatorias, pero sí recomendables.
Incluyen documentos de:
- INCIBE
- CCN-CERT (Guías STIC)
- ENISA
- ECSO
## **Estándares de securización en sistemas y redes**
Son normativas técnicas de aplicación repetitiva, útiles para certificaciones:
### ISO relevantes:
- ISO/IEC 27000 - SGSI
- ISO/IEC 27032 - Ciberseguridad
- ISO/IEC 27033 - Seguridad de redes
- ISO/IEC 27034 - Seguridad en aplicaciones
- ISO/IEC 27035 - Gestión de incidentes
- ISO/IEC 27036 - Seguridad con terceros
### NIST CSF
Framework ampliamente utilizado.
Se menciona también el ENS, obligatorio para la administración pública española y proveedores.
## **Caracterización de procedimientos, instrucciones y recomendaciones**
Explica cómo documentar un procedimiento, por ejemplo el de gestión de incidentes:
- Nombre
- Propietario
- Objetivos
- Entradas y salidas
- Recursos humanos y técnicos
- Mecanismos de control
- Indicadores (clave para medir la eficacia)
![[modeloCaracterizacion.png]]
## **Niveles, escalado y protocolos de atención a incidencias**
Diferencia entre:
- Evento: cualquier cambio significativo en un sistema TIC, puede ser solo una notificación o alerta
- Evento de seguridad: evento que indica que se ha incumplido una política o regla de seguridad
- Incidente de seguridad: uno o varios eventos de seguridad que suponen un riesgo real para los sistemas o la información de la organización
Se detalla:
- Importancia de clasificar incidentes según criticidad
- Uso de taxonomías como la de INCIBE
- Escalado según niveles (ej: Nivel 1 -> incidentes bajos; Nivel 2 -> críticos)
- Un incidente puede cerrarse sin resolverse (ej: ransomware sin copia de seguridad)
- Necesidad de indicadores para mejorar el servicio