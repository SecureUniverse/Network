# MetaSploit

## Initialize
- Database settings
  - ```systemctl start postgresql```
  - ```msfdb init```
- Run
  - ```msfconsole```  

## Workspace
- Create
  - ```workspace -a nasa``` 
- Delete
  - ```workspace -d nsa```
- Show
  - ```workspace```  
- Go to a workspace
  - ``` workspace nasa```










Input from nmap
- ```nmap -sV -oX output.xml 192.168.3.5```
- ```searchsploit --nmap output.xml```
