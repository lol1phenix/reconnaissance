# nmap cheatsheet

### TCP
- TCP scan (for non root users too)
```
nmap -sT <ip>
```

- SYN scan - SYN, SYN/ACK, RST - root only
```
nmap -sS <ip>
```

- Null scan - stealth - all flags are 0
```
nmap -sN <ip>
```

- FIN scan -sends with fin flag from beginning - stealh
```
nmap -sF <ip>
```

- XMAS scan - mixing the flags to wrong one so app will RST if open - stealth
```
nmap -sX <ip>
```

- XMAS

### UDP
- UDP scan
```
nmap -sU <ip>
```

- 100 most common ports to scan only
```
nmap -sU -F <ip>
```

### Other
- Port specification
```
nmap -p22
nmap -p22,80
nmap -p1-1023
nmap -p- <ip>  #all ports
```

- Timing 0-slowest, 5 fastest scan, avoid IDS =0,1, 
```
nmap -T<0-5>
```