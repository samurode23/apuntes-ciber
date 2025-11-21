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
- Antimalware: soluciones básicas (antivirus) que hoy incluyen funciones adicionales como cortafuegos
- EDR y XDR: versiones avanzadas del antimalware con capacidades predictivas y reactivas basadas en IA
- Firewalls: controlan y filtran el tráfico entre redes según reglas configuradas
- Copias de seguridad: permiten recuperar la información ante pérdidas o ataques; son esenciales en contingencia
- DLP: previenen fugas de datos controlando qué información puede salir de la organización
- Verificación de integridad: detectan cambios no autorizados en archivos mediante hashes y alertas
- Conexiones seguras (VPN): protegen la confidencialidad del tráfico cifrando las comunicaciones
- IDS: detectan comportamientos anómalos en red o hosts y alertan antes de una intrusión
- Virtual patching: protege sistemas obsoletos o no actualizables bloqueando amenazas conocidas
- SIEM: centralizan y correlacionan eventos para identificar actividades sospechosas en tiempo real
### Reactivas
- EDR y XDR: sistemas avanzados que pueden contener, bloquear o eliminar amenazas detectadas usando motores de inferencia muy eficaces
- IPS: versión reactiva de un IDS; además de detectar, bloquea eventos no autorizados
- Plan de contingencia: política que agrupa herramientas (copias de seguridad, gestión de incidentes, etc.) para restaurar la actividad de la organización tras un incidente
- Verificación de integridad: además de prevenir cambios no autorizados, puede restaurar archivos alterados
- Virtual patching: mecanismo que bloquea amenazas cuando no es posible aplicar parches tradicionales, protegiendo sistemas vulnerables
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
- Auditoría de sistemas: revisiones periódicas para detectar problemas derivados de la evolución de sistemas y aplicaciones
- Antimalware: obliga a usar soluciones antivirus/antimalware, ya sean individuales o centralizadas
- Uso de dispositivos móviles y equipos corporativos: directrices técnicas para proteger el hardware corporativo
- Control de acceso: define roles y permisos siguiendo modelos como Zero Trust, evitando accesos innecesarios
- Copias de seguridad: protege la información crítica ante pérdidas, integrándose en la continuidad de negocio
- Gestión de logs: permite monitorizar alertas y analizar errores o incidentes para responder más rápido
- Respuesta a incidentes: establece un plan claro y un sistema de escalado para actuar ante incidentes inevitables
- Actualizaciones: regula cómo desplegar parches y actualizaciones para evitar vulnerabilidades explotables
- Borrado seguro: define cómo eliminar datos de forma irrecuperable, ya sea por necesidad o cumplimiento legal
- Teletrabajo: fija medidas para trabajar de forma segura desde fuera de la empresa (VPN, 2FA, etc.)
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
- Nombre del proceso: gestión de incidentes
- Propietario: CISO (responsable del proceso)
- Destinatarios: usuarios, personal y clientes
- Objetivo: recibir incidentes (correo, llamadas, formulario), procesarlos mediante RTIR y obtener indicadores que permitan medir eficacia y eficiencia
- Entradas: colas de correo, llamadas telefónicas y formularios web
- Salidas: informes, estadísticas y otros resultados del proceso
- Recursos humanos: un responsable, tres técnicos de nivel 1 y uno de nivel 2
- Recursos tecnológicos: RTIR, máquinas de pruebas, sandboxes y paneles Kibana
- Mecanismos de control: informes de seguimiento y tiempos de respuesta
- Indicadores: incidentes resueltos por día, tiempo medio de resolución, etc.
    - Son esenciales, ya que lo que no se mide, no se puede mejora
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