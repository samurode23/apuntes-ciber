## **Orígenes**
- 70: 
	- Casi no existía preocupación por la seguridad lógica
	- Aparecen los primeros virus experimentales
	- CERT (Computer Emergency Response Team)
	- CIRT (Computer Incident Response Team)
	- CSIRT (Computer Security Information Response Team)
- 80: 
	- La informática empieza a popularizarse
	- Las amenazas lógicas se vuelven más relevantes (primeros gusanos (Morris), malware básico)
	- Surgen riesgos derivados de redes más interconectadas y del auge del software comercial
- 2000: 
	- Aumento masivo de incidentes debido a:
		- Internet global
		- Smartphones
		- Cloud computing
		- IoT (Internet of Things)
	- Los ataques se vuelven más sofisticados
	- Se crean servicios colaborativos, mejores herramientas defensivas y nuevas normativas
## Necesidad del bastionado
El bastionado es necesario para:
- Proteger las tres dimensiones de la seguridad: 
	- Confidencialidad: garantiza que la información solo es accesible por las personas, sistemas o procesos autorizados. Evita accesos no permitidos y fugas de datos
	- Integridad: asegura que los datos no han sido alterados, manipulados o borrados de forma no autorizada. La información debe mantenerse completa, exacta y consistente
	- Disponibilidad: garantiza que la información, sistemas y servicios están accesibles cuando los usuarios los necesitan. Implica evitar caídas, interrupciones o ataques como DDoS
	- Autentificación: proceso mediante el cual un sistema verifica que un usuario o dispositivo es realmente quien dice ser. Se realiza con contraseñas, certificados, tarjetas, biometría o MFA
	- No repudio: impide que una persona o entidad pueda negar haber realizado una acción, como enviar un mensaje o firmar un documento. Se logra mediante firmas digitales, registros auditados o certificados
- Cumplir con normativas como el RGPD, que exige cifrado y medidas de protección
- Reducir riesgos ante amenazas como malware, fraudes, insiders o ataques externos
- Corregir vulnerabilidades (fallos de software, configuraciones incorrectas, credenciales por defecto)
### Tipos de malware (malicious software)
#### Ransomware
**Qué es**: malware que cifra tus archivos o bloquea sistemas y exige un rescate (normalmente dinero) para restaurar el acceso.  
**Cómo actúa:** suele entrar por phishing, exploits o RDP abierto; una vez dentro cifra datos y deja instrucciones.  
**Impacto:** pérdida de datos, interrupción de operaciones, costes económicos y reputacionales.  
**Defensa:** backups offline y probados, parchear sistemas, segmentación de red, formación anti-phishing, detección/EDR.
#### Spyware
**Qué es:** software diseñado para espiar, recopila información (credenciales, historial, actividad) y la envía al atacante.  
**Cómo actúa:** se instala con instalaciones aparentemente legítimas, extensiones maliciosas o vulnerabilidades.  
**Impacto:** robo de identidad, violación de privacidad, filtración de datos sensibles.  
**Defensa:** antivirus/antimalware actualizado, revisar permisos de apps/extensiones, evitar software pirata, políticas de privacidad.
#### Troyanos (Trojan horses)
**Qué es:** programas que se presentan como útiles/legítimos pero contienen código malicioso oculto.  
**Cómo actúa:** usuario los instala (ingeniería social); luego permiten puertas traseras, robo de datos o descarga de más malware.  
**Impacto:** acceso remoto, robo de credenciales, pivotaje dentro de la red.  
**Defensa:** validar firmas/certificados, escanear descargas, principio de mínimo privilegio, EDR.
#### Gusanos (worms)
**Qué es:** malware autorreplicante que se propaga por redes o Internet sin intervención humana.  
**Cómo actúa:** explota vulnerabilidades (p. ej. de servicios de red) para copiarse a otros equipos y ejecutarse.  
**Impacto:** tráfico masivo, denegación de servicio, propagación de carga útil (p.ej. ransomware).  
**Defensa:** parches rápidos, cortafuegos, segmentación de red, sistemas de detección de intrusos.
#### Bots/Botnets
**Qué es:** dispositivos infectados por un “bot” controlado por un atacante; muchos bots forman una botnet.  
**Cómo actúa:** el bot recibe órdenes (C2) y puede lanzar ataques DDoS, enviar spam o minar cripto.  
**Impacto:** abusos en gran escala, ataques coordinados, uso de recursos.  
**Defensa:** detección de tráfico anómalo, cierre de puertos innecesarios, parcheo, listas de bloqueo.
#### Keyloggers
**Qué es:** software o hardware que registra las teclas pulsadas para capturar contraseñas y otros datos.  
**Cómo actúa:** se instala en el sistema (malware) o se conecta físicamente al equipo; envía registros al atacante.  
**Impacto:** robo de credenciales, acceso a cuentas.  
**Defensa:** autenticación multifactor (MFA), antivirus, teclado en pantalla para transacciones sensibles, revisar dispositivos conectados.
#### Rootkits
**Qué es:** conjunto de técnicas y herramientas para ocultar la presencia de malware y mantener privilegios de sistema (normalmente a nivel kernel).  
**Cómo actúa:** modifica el sistema operativo para esconder procesos/archivos/actividad y resistir detección.  
**Impacto:** compromiso profundo y persistente, muy difícil de erradicar sin reinstalar el sistema.  
**Defensa:** integridad de archivos (HIDS), arranque seguro (Secure Boot), parches, reinstalación limpia si se confirma infección.
#### Fileless malware
**Qué es:** malware que opera en memoria o usando herramientas legítimas del sistema (p. ej. PowerShell, WMI) sin dejar archivos en disco. 
**Cómo actúa:** ejecuta código directamente en memoria o reutiliza binarios legítimos para evitar detección basada en archivos.  
**Impacto:** difícil de detectar con antivirus tradicional; persistencia y movimientos laterales.  
**Defensa:** monitorización de comportamientos, EDR/telemetría, restringir uso de herramientas administrativas, parches.
#### Programas "conejo" / "bacterias" (rabbit programs / fork bombs)
**Qué es:** programas que se replican muy rápidamente consumiendo recursos (CPU, memoria, procesos) hasta agotar el sistema.  
**Cómo actúa:** crean muchos procesos/threads o copias de sí mismos; son generalmente una forma de denegación de servicio local.  
**Impacto:** sistema inutilizable por consumo de recursos; pérdida de disponibilidad.  
**Defensa:** límites de recursos (ulimits), controles de procesos, monitorización, políticas de ejecución.
#### Bombas lógicas (logic bombs)
**Qué es:** código que permanece inactivo hasta que se cumple una condición (fecha, evento, eliminación de empleado), cuando entonces ejecuta acciones dañinas.  
**Cómo actúa:** se infiltra en software legítimo y se activa en la condición preprogramada (borrar archivos, cifrar, etc.).  
**Impacto:** daños dirigidos y con timing, difíciles de anticipar.  
**Defensa:** control de cambios en el código, revisiones de integridad, auditorías de código, segregación de funciones, backups.
### Vulnerabilidad
- **CVE (Common Vulnerabilities and Exposures)** es un sistema que asigna un **identificador único y público** a cada vulnerabilidad de seguridad descubierta en software o hardware, permitiendo que empresas, investigadores y usuarios hablen de la misma falla de forma estandarizada. Cada CVE describe de manera breve el problema, su causa y posibles impactos. Ej. CVE-2021-44228.
- **CVSS (Common Vulnerability Scoring System)** es un **sistema de puntuación** que mide la **gravedad o impacto** de una vulnerabilidad (como las registradas en CVE) mediante una escala del **0 al 10**, donde 10 indica la mayor criticidad. El CVSS evalúa factores como la facilidad de explotación, el nivel de acceso requerido, el impacto sobre la confidencialidad, integridad y disponibilidad del sistema, y se usa para **priorizar la gestión de parches y riesgos**. Ej. 10 critical.
## **Bastionado o “Hardening”**
Proceso destinado a reducir o mitigar vulnerabilidades mediante medidas técnicas, organizativas y de configuración.
![[esquemaSeguridad.png]]
Incluye:
- Eliminar cuentas y contraseñas por defecto.
- Actualizar sistemas y aplicar parches.
- Instalar firewalls, WAFs y otros sistemas defensivos.
- Deshabilitar servicios y puertos innecesarios.
- Crear políticas de copias de seguridad y planes de contingencia.
- Elevar seguridad en redes inalámbricas.
- Limitar funciones del sistema para reducir su superficie de ataque.
![[capasDefenda.png]]
Diferencia clave:
- Amenaza: posibilidad de sufrir daño.
- Vulnerabilidad: fallo que permite que la amenaza se materialice.
### Zero Trust
Evolución del modelo de mínimo privilegio. Surge por:
- Teletrabajo
- Movilidad
- Infraestructuras híbridas (nube + on-premise)
- IoT y ampliación del perímetro de red
- Principio básico: “No confíes en nadie por defecto, ni siquiera en la red interna”.
Características:
- Autenticación MFA/2FA
- Control estricto de flujos de red
- Acceso a aplicaciones en vez de acceso a toda la red
- Privilegios mínimos
- Detección avanzada de amenazas (incluidas zero-day)
- VPNs transparentes
### ¿Por dónde empiezo?
Siempre con un análisis de riesgos.
Antes de implementar medidas, se debe:
- Identificar procesos críticos
- Evaluar impacto y probabilidad de amenazas
- Alinear la seguridad con la estrategia del negocio
- Priorizar medidas según riesgo real, no por intuición
Herramientas como el autodiagnóstico de INCIBE ayudan a evaluar personas, procesos y tecnologías.
## **Plan director de seguridad**
Documento estratégico que define cómo mejorar, mantener y gestionar la seguridad de una organización.
Incluye:
- Medidas técnicas y organizativas
- Definición clara del alcance
- Priorización según criticidad
- Alineación con el negocio
- Ciclos de mejora continua (por ejemplo, PDCA / Deming)
![[planDirector.png]]
Basado en marcos como:
- ISO 27001
- NIST Cybersecurity Framework
- ENS (Esquema Nacional de Seguridad)
- PCI-DSS