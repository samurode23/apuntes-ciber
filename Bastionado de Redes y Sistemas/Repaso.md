![[bastionado-de-redes-y-sistemas-1.webp]]


| _TCP/IP_   | _OSI_                                | _Nombre de PDU_ | _Dispositivos_                | _Protocolos_                                                               | _Direcciones_             | _Ataques_             |
| ---------- | ------------------------------------ | --------------- | ----------------------------- | -------------------------------------------------------------------------- | ------------------------- | --------------------- |
| Aplicación | Aplicación<br>Presentación<br>Sesión | Datos           | Gateway<br>Servidores<br>NGFW | DNS<br>HTTP/S<br>FTP/S<br>IMAP<br>DHCP<br>SSH<br>SMTP<br>POP3              |                           | SQL inyection<br>XSS  |
| Transporte | Transporte                           | Segmento        |                               | TCP(seguro)<br>UDP(rápido)                                                 | Puertos 65535 (2^16)      | DDOS                  |
| Internet   | Red                                  | Paquete         | Router<br>Firewall            | IPv4<br>IPv6<br>ICMP<br>ARP                                                | Direcciones IP o lógicas  | DDOS<br>IP spoofing   |
| Subred     | Enlace de datos<br>Física            | Trama           | Switch<br>Access Point        | ARP<br>IEEE 802.3(Ethernet)<br>IEEE 802.11(Wifi)<br>IEEE 802.15(Bluetooth) | Direcciones Mac o físicas | ARP spoofing <br>MITM |

