# NESSUS

## Default Ports
```cat /opt/nessus/var/nessus/nessus-service | wc```

New Scan -> Advanced Scan -> Settings -> DISCOVERY -> Port Scanning -> Ports: Port scan range

## Run
```cd /opt/nessus/sbin``` & ```./nessusd```

## Aggressive Scan
- New Scan / Advanced Scan
  - Settings
    - ASSESSMENT
      - General
        - Accuracy: Perform thorough tests …
      - Web Applications
      - Malware 
    - REPORT 
      - Override normal …
      - Show missing …
    - ADVANCED
      - General Setting: Enable safe …

## IP Setting
```nano /etc/netplan/50-cloud-init.yaml```
- addresses : \["a.b.c.d"\]
- dhcp4 : false
- gateway4 : a.b.c.1

```apply netplan```

## Free
[Resource1](https://www.cnblogs.com/4geek/p/12896562.html), [Resource2](https://blog.csdn.net/guopiao/article/details/114136550), [Resource3](https://blog.csdn.net/lodossboy/article/details/106605915), [Resource4](https://mrxn.net/hacktools/659.html)

1. Internet access to Kali VM
   - Add *"web filter"* in *"internet firewall"* for *"\*.tenable.com"* & *"\*.nessus.org"*
2. Change DNS
   - Add Shekan DNS to *"etc/resolv.conf"*
3. Installation
   - Register in *"tenable.com"* with fake mail
   - Download *"deb"* file from link in Email
   - Save the *"Activation Code"* fro download plugins in offline mode
   - ```dpkg -i Nessus-8.10.0-debian6_amd64.deb```
4. Run
   - Start Nessus: ```/bin/systemctl start nessusd.service```
   - Open in Web browser: "https://127.0.0.1:8834"
5. Download plugins
   - Go to: Managed Scanner > Tenable.sc
   - Find challenge code: ```/opt/nessus/sbin/nessuscli fetch --challenge``` 
   - Add *"challenge code"* & *"activation code"* to this address: "https://plugins.nessus.org/v2/offline.php"
   - Install plugins
     - ```/opt/nessus/sbin/nessuscli update all-2.0.tar.gz``` 
6. Upgrade to Pro
   - Create tese two files
     - ```touch /opt/nessus/lib/nessus/plugins/plugin_feed_info.inc```
     - ```touch /opt/nessus/var/nessus/plugin_feed_info.inc```
   - Open above files with nano and add these commands (first line is the data & time of install)
```
PLUGIN_SET = "202108051247";
PLUGIN_FEED = "ProfessionalFeed (Direct)";
PLUGIN_FEED_TRANSPORT = "Tenable Network Security Lightning";
```  
7. Restart Nessus
8. If no plugins
   - Install *"Essentials"* & update it to add *"plugins"* directory
   - Copy and save the directory
   - Do step 1 to 7
   - Add above directory to new installed app (twice till nessus not can remove it)
     - ```/opt/nessus/lib/nessus/plugins```
     - ```/opt/nessus/lib/nessus/plugins/plugins```
