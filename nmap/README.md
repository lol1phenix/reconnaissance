# nmap cheatsheet

- TCP scan (for non root users too)
```
nmap -sT <ip>
```

- SYN scan - SYN, SYN/ACK, RST - root only
```
nmap -sS <ip>
```

- UDP scan
```
nmap -sU <ip>
```