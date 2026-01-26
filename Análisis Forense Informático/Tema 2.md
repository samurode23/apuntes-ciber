## 1. Autopsy
Get-FileHash C:\Users\Alumno\Downloads\ejemplo.iso -Algorithm MD5
### 1.1. Recent Activity
Reconstruye la actividad reciente del usuario
Extrae:
- Programas ejecutados
- Historial de navegación
- Archivos abiertos recientemente
- USB conectados
- Búsquedas
- Jump Lists
Usa artefactos como NTUSER.DAT, SYSTEM, navegadores  
Es uno de los más importantes (casi siempre activado)
### 1.2. Hash Lookup
Compara hashes de archivos
- Detecta archivos conocidos
- Usa bases como:
	- NSRL (archivos legítimos)
	- Listas de malware
Sirve para:
- Filtrar ruido
- Detectar archivos maliciosos conocidos
### 1.3. File Type Identification
Identifica el tipo real del archivo
- No se fía de la extensión
- Analiza la cabecera (magic number)
Ejemplo:
- foto.jpg.exe -> ejecutable
- doc.pdf que en realidad es un ZIP
### 1.4. Extension Mismatch Detector
Detecta archivos con extensión falsa
Compara:
- Extensión
- Tipo real
Muy útil para:
- Malware
- Ocultación de archivos
### 1.5. Embedded File Extractor
Extrae archivos incrustados
Extrae contenido de:
- PDFs
- DOCX
- PPTX
- ZIPs
- Correos
Ejemplo:
- PDF con un EXE dentro
- DOC con imágenes ocultas
### 1.6. Picture Analyzer
Analiza imágenes
Detecta:
- Rostros
- Clasificación básica de imágenes
Soporte para investigaciones visuales
Usado en:
- CSAM
- Análisis de imágenes sospechosas
### 1.7. Keyword Search
Busca palabras clave
- En archivos
- En texto eliminado
- En slack space
Ejemplo:
- “bomba”
- “arma”
- nombres, correos, lugares
Puede tardar bastante
### 1.8. Email Parser
Analiza correos electrónicos
Soporta:
- PST
- OST
- MBOX
- EML
Extrae:
- Remitente
- Destinatario
- Adjuntos
- Fechas
### 1.9. Encryption Detection
Detecta archivos cifrados
- Alta entropía
- Volúmenes cifrados
- Contenedores protegidos
No descifra, solo detecta
### 1.10. Interesting Files Identifier
Marca archivos “interesantes”
Busca:
- .exe
- .bat
- .ps1
- .zip
- herramientas hacking
Ideal para priorizar análisis
### 1.11. Central Repository
Correlación entre casos
Compara:
- Hashes
- Usuarios
- Dispositivos
Detecta reincidencias
Usado en laboratorios policiales
### 1.12. PhotoRec Carver
Recupera archivos borrados
- File carving
- No usa sistema de archivos
Recupera:
- Fotos
- Vídeos
- Documentos
Útil cuando el FS está dañado
### 1.13. Virtual Machine Extractor
Detecta máquinas virtuales
Busca:
- VDI
- VMDK
- VHD
Muy usado para evasión o laboratorios ocultos
### 1.14. Data Source Integrity
Verifica integridad
- Hashes
- Asegura que la imagen no se ha modificado
Fundamental en informes periciales
### 1.15. Android Analyzer (aLEAPP)
Análisis forense Android
Extrae:
- WhatsApp
- SMS
- Llamadas
- Apps
- Ubicaciones
### 1.16. Cyber Triage Malware Scanner
Detección rápida de malware
- Basado en reglas y heurística
- Ideal para triaje inicial
### 1.17. DJI Drone Analyzer
Analiza drones DJI
Extrae:
- Rutas de vuelo
- Ubicación GPS
- Fotos y vídeos
### 1.18. Plaso
Genera líneas temporales avanzadas
- Supera la timeline básica
- Correlaciona múltiples fuentes
Muy potente para reconstrucción de hechos
### 1.19. YARA Analyzer
Escaneo con reglas YARA
- Detecta malware específico
- Coincidencias binarias
Nivel avanzado/profesional
### 1.20. iOS Analyzer (iLEAPP)
Forense iOS
- Chats
- Llamadas
- Apps
- Ubicación
### 1.21. GPX Parser
Analiza rutas GPS
- GPX
- Tracks
- Coordenadas
### 1.22. Android Analyzer
Segundo analizador Android  
(similar a aLEAPP, depende versión)

## 2. Regripper
![[Captura de pantalla 2026-01-15 013857.png]]
### 2.1. Ejecución de programas y evidencias de uso
Estos te dicen **qué se ejecutó**, **cuándo**, o **qué apps se usaron**:
- userassist/userassist_tln: programas ejecutados desde el GUI (explorador/menú inicio), con contadores y timestamps
- bam/ bam_tln: Background Activity Moderator: rastro de ejecución/uso de apps por usuario (muy útil en Win10/11)
- appcompatcache/ shimcache (+ `_tln`): “ShimCache” del SYSTEM hive: rastros de ejecución/presencia de binarios (ojo: no siempre implica ejecución real)
- amcache/amcache_tln: inventario de ejecutables instalados/ejecutados (hashes, rutas, primera vez visto)
- recentapps (+ _tln): apps recientes usadas
- muicache: lista de ejecutables vistos por el sistema (nombres amigables)
### 2.2. Persistencia/Autostart (para malware y triage)
Plugins que buscan **arranques automáticos** o técnicas de persistencia:
- run, run_tln: claves Run/RunOnce (HKLM/HKCU)
- cmdproc: Command Processor\AutoRun (persistencia por CMD)
- appinitdlls: AppInit_DLLs (inyección DLL clásica)
- appcertdlls: AppCertDlls (carga de DLLs al ejecutar apps)
- imagefile: Image File Execution Options (debugger hijack, etc.)
- netsh: DLLs helper de NetSH (persistencia/abuso)
- printmon: Print Monitors (persistencia vía spooler)
- tasks/taskcache (+ `_tln`): tareas programadas (root o lista)
- termserv, rdpport: configuración de Terminal Services/RDP
- uacbypass: señales/configs típicas para bypass UAC
### 2.3. Actividad del usuario (MRUs, recientes, historial “humano”)
Esto es oro para reconstruir qué hizo el usuario:
- runmru: comandos ejecutados en “Ejecutar…” (Win+R)
- typedpaths: rutas tecleadas en Explorer
- typedurls/typedurlstime: URLs escritas en IE/Edge legado (con tiempos en algunos casos)
- recentdocs (+ _tln): documentos abiertos recientemente (por extensión)
- comdlg32: “Open/Save As” dialogs: archivos abiertos/guardados desde apps
- wordwheelquery: búsquedas del cuadro de búsqueda (Explorer/Start)
- jumplistdata: rastros de Jump Lists (lo que se abrió anclado/reciente)
- mmc: consolas MMC usadas recientemente
- msoffice: MRUs y paths de Office (Word/Excel/PowerPoint, según versión)
- sevenzip, winrar, winzip: historiales de compresión/extracción
### 2.4. Dispositivos USB y hardware conectado
Para “¿conectó un USB?” y cuándo:
- usbstor: info de dispositivos USB storage
- usbdevices: Enum\USB y WPD (más amplio)
- usb: resumen USB
- mountdev/mountdev2: MountedDevices (letras <-> volúmenes)
- devclass: DeviceClasses (USB y más; conexiones)
- mp2(MountPoints2): qué unidades/removibles vio el usuario (HKCU)
### 2.5. Red, Wi-Fi, IPs, perfiles de red
Para “¿a qué redes se conectó?”:
- networklist (+ _tln): perfiles de red (SSID/nombre red, tipo, timestamps)
- ips: IPs, DHCP, dominios
- nic2/networkcards: tarjetas de red
- routes: rutas persistentes
- ssid: info SSID (depende servicio/versión)
### 2.6. Seguridad/políticas/auditoría
Para postura defensiva o cambios raros:
- auditpol: política de auditoría desde SECURITY hive
- defender: settings de Windows Defender
- pslogging: si PowerShell logging está habilitado (ScriptBlock, Module, Transcription…)
- execpolicy: ExecutionPolicy de PowerShell
- disableeventlog: checks típicos de manipulación/deshabilitado de logs
- disablelastaccess: LastAccessUpdate (impacta a timelines NTFS)
- cred: UseLogonCredential (Wdigest), relevante para robo creds
### 2.7. Cuentas y logon
- samparse (+ _tln): usuarios/grupos locales (SAM)
- lastloggedon: LogonUI last logged on users
- logonstats: stats de logon en NTUSER
- profilelist: perfiles de usuario (SID <-> ruta)
### 2.8. Shellbags y carpetas (movimiento por el Explorador)
- shellbags (+ _tln): evidencia de carpetas vistas/navegadas incluso si ya no existen
- shellfolders: rutas de carpetas especiales
- allowedenum: carpetas especiales/hide
- thispcpolicy: políticas “Este equipo” (ocultar/mostrar)
### 2.9. “Anti-forense”/hallazgos raros en el hive
- del/slack/sizes/baseline/null/rlo: buscan claves borradas, slack space, tamaños anómalos, nombres con caracteres raros (null, RLO)
- fileless/findexes: hunting de malware fileless o binarios embebidos (busca “MZ” en datos binarios)
- inprocserver/scriptleturl/clsid: hunting en COM/CLSID para secuestros de clases

## 3. Archivos importantes
### 3.1. hiberfil.sys
¿Qué es?  
Archivo usado por Windows para la hibernación.
¿Qué guarda?
- Contenido de la RAM cuando el sistema se hiberna
- Procesos en ejecución
- Credenciales en memoria (en algunos escenarios)
- Claves de cifrado, conexiones de red, malware en memoria
Uso forense:
Muy valioso para análisis de memoria y recuperación de información volátil.
¿Dónde está?
C:\
### 3.2. Hives (Registro de Windows)
Los hives son bases de datos del Registro de Windows.
¿Dónde están?
C:\Windows\System32\config\
#### 3.2.1. SYSTEM
- Información del arranque
- Controladores y servicios
- Zona horaria
- Dispositivos conectados
Útil para:
- Saber cuándo se arrancó el sistema
- Detectar drivers maliciosos
#### 3.2.2. SOFTWARE
- Programas instalados
- Versiones de software
- Configuraciones globales
Útil para:
- Detectar software sospechoso o persistencia
#### 3.2.3. SAM
- Cuentas de usuario locales
- Hashes de contraseñas (NTLM)
Útil para:
- Cracking de contraseñas
- Enumeración de usuarios
#### 3.2.4. SECURITY
- Políticas de seguridad
- Derechos de usuario
- Auditoría
Útil para:
- Ver configuraciones de seguridad y permisos
#### 3.2.5. DEFAULT
- Perfil por defecto (pantalla de login)
Poco uso forense, pero aporta contexto
### 3.3. ntuser.dat
¿Qué es?  
Registro específico de cada usuario.
¿Qué guarda?
- Programas ejecutados
- Historial de archivos
- Configuración del escritorio
- Claves Run (persistencia)
Muy importante para:
- Actividad del usuario
- Persistencia de malware
- Línea temporal de acciones
¿Dónde está?
C:\Users\usuario\
### 3.4. UsrClass.dat (Shellbags)
¿Qué es?  
Parte del registro relacionada con el explorador de Windows.
Shellbags permiten saber:
- Carpetas que el usuario abrió, incluso si ya no existen
- Carpetas en discos externos o USB
- Estructura de directorios visitados
Muy potente para:
- Reconstruir navegación por carpeta
- Probar que un usuario accedió a un directorio
¿Dónde está?
C:\Users\usuario\AppData\Local\Microsoft\Windows
### 3.5. EVTX (Event Logs)
¿Qué son?  
Logs de eventos de Windows.
Contienen:
- Inicios y cierres de sesión
- Fallos de autenticación
- Eventos del sistema
- Actividad de servicios
Clave para:
- Detección de intrusiones
- Análisis de incidentes
- Línea temporal
¿Dónde está?
C:\Windows\System32\winevt\Logs\
Ejemplos importantes:
- Security.evtx
- System.evtx
- Application.evtx
### 3.6. Prefetch (.pf)
¿Qué es?  
Archivos creados cuando se ejecuta un programa.
Contienen:
- Nombre del ejecutable
- Ruta
- Últimas ejecuciones
- Número de veces ejecutado
- DLLs cargadas
Muy útil para:
- Saber si un programa se ejecutó
- Detectar malware aunque ya no exista
¿Dónde está?
C:\Windows\Prefetch\
### 3.7. Amcache.hve
¿Qué es?  
Registro que guarda información de ejecutables que se han ejecutado.
Incluye:
- Nombre del archivo
- Ruta
- Hash
- Fecha de ejecución
- Información de dispositivos externos
Excelente para:
- Confirmar ejecución de malware
- Correlación con Prefetch
¿Dónde está?
C:\Windows\AppCompat\Programs\
### 3.8. SRUM (SRUDB.DAT)
¿Qué es?  
Base de datos de uso de recursos del sistema.
Registra:
- Uso de red por aplicación
- Consumo de energía
- Actividad de aplicaciones
- Usuarios asociados a procesos
Muy potente para:
- Saber qué aplicación se conectó a la red
- Detección de exfiltración de datos
¿Dónde está?
C:\Windows\System32\sru\
### 3.9. Jump Lists/LNK
¿Dónde están?
C:\Users\usuario\
#### 3.9.1. LNK (Accesos directos)
- Archivos abiertos
- Ubicación original
- Timestamps
- Volúmenes y discos usados
Útiles para:
- Saber qué archivo abrió el usuario
- Uso de USBs
#### 3.9.2. Jump Lists
- Archivos recientes por aplicación (Word, Explorer, etc.)
- Acciones frecuentes del usuario
Ideales para:
- Reconstruir actividad reciente del usuario

##  4. Volatility
### 4.1. Identificación del sistema
#### 4.1.1 imageinfo (Volatility 2)
    - Detecta el perfil del sistema operativo, arquitectura y fecha de captura
    - Usado para saber que el sistema era Windows 7 SP1 x64
    - Es siempre el primer paso en Volatility 2
#### 4.1.2. windows.info (Volatility 3)
    - Alternativa moderna a imageinfo
    - Proporciona información más precisa del SO
    - Usado junto a imageinfo para confirmar el entorno
### 4.2. Usuarios y sesiones
#### 4.2.1. windows.session
    - Muestra sesiones activas, procesos asociados y tiempos de inicio
    - Usado para:        
        - Saber qué usuario estaba logueado (Administrador)
        - Calcular el tiempo que llevaba encendido el sistema
### 4.3. Procesos y aplicaciones
#### 4.3.1. windows.pslist
    - Lista procesos activos en el momento del volcado
    - Usado para identificar aplicaciones abiertas:
        - chrome.exe
        - notepad.exe
        - cmd.exe
        - explorer.exe
        - dwm.exe
### 4.4. Archivos en memoria
#### 4.4.1. windows.filescan
    - Busca estructuras de archivos en memoria (incluso borrados)
    - Usado para:
        - Encontrar el historial del navegador
        - Localizar archivos sospechosos como ubicaciones descarga material.txt
#### 4.4.2. windows.dumpfiles
    - Extrae archivos desde memoria usando offsets físicos
    - Usado para:
        - Extraer el archivo History
        - Intentar recuperar archivos detectados con filescan
### 4.5. Navegación web/Historial
#### 4.5.1. windows.filescan | grep History
    - Combinación práctica para localizar bases de datos del navegador
    - Permite luego analizar el historial con SQLite
### 4.6. Portapapeles
#### 4.6.1. clipboard (Volatility 2)
    - Extrae el contenido del portapapeles
    - Clave en la práctica:
        - Recuperar el IBAN copiado
        - Evidencia directa de la transferencia bancaria
### 4.7. Credenciales
#### 4.7.1. windows.hashdump
    - Extrae hashes LM/NTLM de usuarios
    - Usado para obtener el hash del usuario Administrador y comprobar si estaba crackeado
### 4.8. Sistema de archivos
#### 4.8.1. mftparser
    - Analiza la MFT de NTFS desde memoria
    - Usado para:
        - Ver la fecha de creación del archivo sospechoso
### 4.9. Análisis de procesos y malware
- psscan -> Detecta procesos ocultos (rootkits)
- pstree -> Árbol de procesos (relaciones padre-hijo)
- malfind -> Código inyectado en procesos 
- dlllist -> DLLs cargadas por proceso
### 4.10. Red
- netscan -> Conexiones de red activas
- connscan -> Conexiones ocultas o cerradas
### 4.11. Credenciales avanzadas
- lsadump -> Secrets del sistema
- credman -> Credenciales almacenadas
- hashdump + john/hashcat -> Ataques offline
### 4.12. Memoria y strings
- yarascan -> Buscar firmas malware
- strings/volatility strings -> Buscar texto sensible
### 4.13. Registro
- printkey -> Claves del registro (autoruns, persistencia)
- userassist -> Programas ejecutados por el usuario
