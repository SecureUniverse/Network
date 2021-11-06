# MetaSploit

## Initialize
- Database settings: ```systemctl start postgresql``` & ```msfdb init```
- Run: ```msfconsole```  

## Workspace
- Create: ```workspace -a nasa``` 
- Delete: ```workspace -d nsa```
- Show: ```workspace```  
- Go to a workspace: ``` workspace nasa```

## Search
```
search type:exploit cve:2019
search type:auxiliary cve:2019
search platform:windows description:chrome
search platform:android description:2019
search platform:exploit description:samsung
```

## Auxiliary
```use  auxiliary/scanner/mongodb/mongodb_login```
```set rhosts 192.168.1.0/24```
```run```


## Exploit


## Meterprete


Input from nmap
- ```nmap -sV -oX output.xml 192.168.3.5```
- ```searchsploit --nmap output.xml```
