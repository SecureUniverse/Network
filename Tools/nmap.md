# Nmap

## Switch
- __Scan techniques__
  - UDP scan: ```-sU```
- __Host discovery__
  - disable port scan (just ping): ```-sn```
  - disable Reverse DNS Resolution: ```-n```
  - avoid host discovery: ```-Pn```
- __Port specification__
  - specific port: ```-p 25```  
  - top ports: ```--top-ports 3```
- __Service & version detection__
  - service version detection: ```-sV```
  - aggresive: ```-A```
  - OS detection: ```-O```
- __Other__
  - input: ```-iL targets.txt```
  - output: ```-oA```
  - debug: ```-d```
  - verbosity (1 to 9): ```-v2```
  - choose interface: ```nmap --iflist``` & ```nmap -e eth0 192.168.3.5```

## NSE
- path: ```/usr/share/nmap/scripts```
- update: ```nmap --script-updatedb```
- search: ```locate *.nse | grep telnet```
- help: ```nmap --script-help smb-brute```
- handy scripts: ```\*-brute.nse``` , ```\*-info.nse``` , ```dns-recursion``` , ```dns-zone-transfer``` , ```http-slowloris-check``` , ```ms-sql-info``` , ```ms-sql-dump-hashes``` , ```nbstat``` , ```smb-enum-users``` , ```smb-enum-shares```
- run all default scripts: ```-sC```

## Firewall Evasion
- send from spoofed IPs: ```-D 5.5.5.5, 6.6.6.6```
- fragmentation: ```-f 192.168.1.99```
- change mac: ```--spoof-mac 24-FD-52-C2-98-6B```
- define src port: ```--source-port 80```
- set own offset size: ```--mtu 32```

## Timing
- extend the duration (0 to 5): ```-T1```
- number of retries: ```--max-retries 2```
- max wait: ```--host-timeout 30m```

## Complete
- live hosts: ```nmap -sn 192.168.3.3/24 -oG - | grep Up | awk ‘{print $2}’ > targets.txt```
- IDS Evasion: ```nmap -f -t 0 -n -Pn –data-length 200 -D 192.168.1.101,192.168.1.102,192.168.1.103,192.168.1.23 192.168.1.1```

## Ports
<img src="images\ports1.png" width="450">
<img src="images\ports2.jpg" width="500">

