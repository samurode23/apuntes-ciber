## __Orígenes__:
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
__Necesidad del bastionado__
El bastionado es necesario para:
- Proteger las tres dimensiones de la seguridad: confidencialidad, integridad y disponibilidad
- Cumplir con normativas como el RGPD, que exige cifrado y medidas de protección
- Reducir riesgos ante amenazas como malware, fraudes, insiders o ataques externos
- Corregir vulnerabilidades (fallos de software, configuraciones incorrectas, credenciales por defecto)

## __Bastionado__ (“Hardening”)
Proceso destinado a **reducir o mitigar vulnerabilidades** mediante medidas técnicas, organizativas y de configuración.
Incluye:
- Eliminar cuentas y contraseñas por defecto.
- Actualizar sistemas y aplicar parches.
- Instalar firewalls, WAFs y otros sistemas defensivos.
- Deshabilitar servicios y puertos innecesarios.
- Crear políticas de copias de seguridad y planes de contingencia.
- Elevar seguridad en redes inalámbricas.
- Limitar funciones del sistema para reducir su superficie de ataque.

**Diferencia clave:**

- **Amenaza:** posibilidad de sufrir daño.
    
- **Vulnerabilidad:** fallo que permite que la amenaza se materialice.
Zeek 
## __Tipos de malware__ (malicious software)
### Ransomware
**Qué es:** Malware que cifra tus archivos o bloquea sistemas y exige un rescate (normalmente dinero) para restaurar el acceso.  
**Cómo actúa:** Suele entrar por phishing, exploits o RDP abierto; una vez dentro cifra datos y deja instrucciones.  
**Impacto:** Pérdida de datos, interrupción de operaciones, costes económicos y reputacionales.  
**Defensa:** backups offline y probados, parchear sistemas, segmentación de red, formación anti-phishing, detección/EDR.

### Spyware
**Qué es:** Software diseñado para espiar, recopila información (credenciales, historial, actividad) y la envía al atacante.  
**Cómo actúa:** Se instala con instalaciones aparentemente legítimas, extensiones maliciosas o vulnerabilidades.  
**Impacto:** Robo de identidad, violación de privacidad, filtración de datos sensibles.  
**Defensa:** antivirus/antimalware actualizado, revisar permisos de apps/extensiones, evitar software pirata, políticas de privacidad.

### Troyanos (Trojan horses)
**Qué es:** Programas que se presentan como útiles/legítimos pero contienen código malicioso oculto.  
**Cómo actúa:** Usuario los instala (ingeniería social); luego permiten puertas traseras, robo de datos o descarga de más malware.  
**Impacto:** Acceso remoto, robo de credenciales, pivotaje dentro de la red.  
**Defensa:** validar firmas/certificados, escanear descargas, principio de mínimo privilegio, EDR.

### Gusanos (worms)
**Qué es:** Malware autorreplicante que se propaga por redes o Internet sin intervención humana.  
**Cómo actúa:** Explota vulnerabilidades (p. ej. de servicios de red) para copiarse a otros equipos y ejecutarse.  
**Impacto:** Tráfico masivo, denegación de servicio, propagación de carga útil (p.ej. ransomware).  
**Defensa:** parches rápidos, cortafuegos, segmentación de red, sistemas de detección de intrusos.

### Bots / Botnets
**Qué es:** Dispositivos infectados por un “bot” controlado por un atacante; muchos bots forman una botnet.  
**Cómo actúa:** El bot recibe órdenes (C2) y puede lanzar ataques DDoS, enviar spam o minar cripto.  
**Impacto:** abusos en gran escala, ataques coordinados, uso de recursos.  
**Defensa:** detección de tráfico anómalo, cierre de puertos innecesarios, parcheo, listas de bloqueo.

### Keyloggers
**Qué es:** Software o hardware que registra las teclas pulsadas para capturar contraseñas y otros datos.  
**Cómo actúa:** Se instala en el sistema (malware) o se conecta físicamente al equipo; envía registros al atacante.  
**Impacto:** Robo de credenciales, acceso a cuentas.  
**Defensa:** autenticación multifactor (MFA), antivirus, teclado en pantalla para transacciones sensibles, revisar dispositivos conectados.

### Rootkits
**Qué es:** Conjunto de técnicas y herramientas para ocultar la presencia de malware y mantener privilegios de sistema (normalmente a nivel kernel).  
**Cómo actúa:** Modifica el sistema operativo para esconder procesos/archivos/actividad y resistir detección.  
**Impacto:** Compromiso profundo y persistente, muy difícil de erradicar sin reinstalar el sistema.  
**Defensa:** integridad de archivos (HIDS), arranque seguro (Secure Boot), parches, reinstalación limpia si se confirma infección.

### Fileless malware
**Qué es:** Malware que opera en memoria o usando herramientas legítimas del sistema (p. ej. PowerShell, WMI) sin dejar archivos en disco.  
**Cómo actúa:** Ejecuta código directamente en memoria o reutiliza binarios legítimos para evitar detección basada en archivos.  
**Impacto:** Difícil de detectar con antivirus tradicional; persistencia y movimientos laterales.  
**Defensa:** monitorización de comportamientos, EDR/telemetría, restringir uso de herramientas administrativas, parches.

### Programas "conejo" / "bacterias" (rabbit programs / fork bombs)
**Qué es:** Programas que se replican muy rápidamente consumiendo recursos (CPU, memoria, procesos) hasta agotar el sistema.  
**Cómo actúa:** Crean muchos procesos/threads o copias de sí mismos; son generalmente una forma de denegación de servicio local.  
**Impacto:** Sistema inutilizable por consumo de recursos; pérdida de disponibilidad.  
**Defensa:** límites de recursos (ulimits), controles de procesos, monitorización, políticas de ejecución.

### Bombas lógicas (logic bombs)
**Qué es:** Código que permanece inactivo hasta que se cumple una condición (fecha, evento, eliminación de empleado), cuando entonces ejecuta acciones dañinas.  
**Cómo actúa:** Se infiltra en software legítimo y se activa en la condición preprogramada (borrar archivos, cifrar, etc.).  
**Impacto:** Daños dirigidos y con timing, difíciles de anticipar.  
**Defensa:** control de cambios en el código, revisiones de integridad, auditorías de código, segregación de funciones, backups.

## Vulnerabilidad
**CVE (Common Vulnerabilities and Exposures)** es un sistema que asigna un **identificador único y público** a cada vulnerabilidad de seguridad descubierta en software o hardware, permitiendo que empresas, investigadores y usuarios hablen de la misma falla de forma estandarizada. Cada CVE describe de manera breve el problema, su causa y posibles impactos. Ej. CVE-2021-44228

**CVSS (Common Vulnerability Scoring System)** es un **sistema de puntuación** que mide la **gravedad o impacto** de una vulnerabilidad (como las registradas en CVE) mediante una escala del **0 al 10**, donde 10 indica la mayor criticidad. El CVSS evalúa factores como la facilidad de explotación, el nivel de acceso requerido, el impacto sobre la confidencialidad, integridad y disponibilidad del sistema, y se usa para **priorizar la gestión de parches y riesgos**. Ej. 10 critical