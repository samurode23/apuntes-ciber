Hash: 
- ¿Qué es? Función matemática con un algoritmo (resumen en n bits y hexadecimal)
- Propiedades: 
	- Finalista: misma entrada -> misma salida
	- Único: no tiene colisiones
	- Unidireccional: A da B pero con B no sacas A
	- Pequeños cambios en input, grandes cambios en output
	- Independientemente del tamaño del input, siempre tiene el mismo tamaño el output -> depende del algoritmo que usemos (md5, SHA1, SHA256, SHA512,...)
- ¿Para que sirve? 
	- Verifica la integridad y autenticidad del archivo 
	- Antivirus/Firewall/IDS/IPS: mediante el hash, compara ese hash con los hash de virus en una base de datos
	- Passwords: compara el hash guardado con el hash de la contraseña introducida
Cifrar:
- Algoritmo oculto: 
	- César
	- Escítala
		- Enigma
- Algoritmo conocido pero clave oculta: 
	- Simétrica: se envía el mensaje con la clave secreta y al recibirlo, si tienes la clave, sacas el mensaje
		- Es muy rápido
		- AES
	- Asimétrico: cada uno tiene una clave privada y una pública, envías el mensaje con la publica del otro y ya el otro con su privada saca el mensaje
		- Es muy lento
		- RSA (Ronald Rivest, Adi Shamir y Leonard Adleman)
	- Híbrido: con la clave pública, se cifra la clave privada para enviarla
		- Es medio rápido
Firma digital
- A un archivo le haces el hash (resumen) y eso lo firmas con tu clave pública (obtienes el resumen cifrado) y envías el archivo con el resumen cifrado. El receptor le hace el hash (resumen) al archivo obtenido y lo compara descifrando el resumen cifrado que le enviaron