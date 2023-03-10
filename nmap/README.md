# nmap cheatsheet

## TCP

- TCP scan (for non root users too)
  
```shell
nmap -sT <ip>
```

- SYN scan - SYN, SYN/ACK, RST - root only

```shell
nmap -sS <ip>
```

- Null scan - stealth - all flags are 0

```shell
nmap -sN <ip>
```

- FIN scan -sends with fin flag from beginning - stealh

```shell
nmap -sF <ip>
```

- XMAS scan - mixing the flags to wrong one so app will RST if open - stealth

```shell
nmap -sX <ip>
```

- ACK scan - all answers are RST, good if there is FW before and see what ports FW is not answering
- Window scan - same purpose - using ACK but checking window size of returned RST

```shell
nmap -sA <ip>
namp -sW <ip>
```

- Custom scans - manipulate Flags as wanted - unexpected results

```shell
nmap --scnaflags SYNFINACKPSH <ip>
```

- Version detection for open ports - require 3way handshake - possible to got for test intensity 0(light)-9

```shell
nmap -sV <ip>
nmap -sV --verion-light <ip> #intensity 2
nmap -sV --version-intensity <0-9> <ip>
```

## UDP

- UDP scan

```shell
nmap -sU <ip>
```

- 100 most common ports to scan only

```shell
nmap -sU -F <ip>
```

## Other

- Port specification

```shell
nmap -p22
nmap -p22,80
nmap -p1-1023
nmap -p- <ip>  #all ports
```

- Timing 0-slowest, 5 fastest scan, avoid IDS =0,1

```shell
nmap -T<0-5>
```

- Spoofed IP - nmap results are sent to SPOOFED_IP, monitoring the network is key to see results
  
```shell
nmap -S<SPOFFED_IP> <IP>
```

- Spoofed MAC - used the same as above but in same subnet

```shell
nmap --spoofed-mac <MAC_ADDR> <IP>
```

- Decoy - similair to spoofed, can be added as multiple IPs to hide attacher IP in multiple requests

```shell
nmap -D <DECOY1_IP,MY_IP,DECOY2_IP> <IP>
nmap -D 10.10.1.1,10.10.1.2,ME <ip> # ME - used to replace local IP
```

- Fragmented packets - brake into pieces to avoid IDS or some FW

```shell
nmap -f -sS <ip>   # 8byte fragments
nmap -ff -sS <ip>  # 16byte fragments
nmap --data-length <bytes> <ip>  #custom size of data appended to packet
```

- Reason - add one more column to show why answer was succesful, visible in verbose too

```shell
nmap -sS --reason <ip>
nmap -sS -vv <ip>
```

- OS detection - add possible OS guess running on that node

```shell
nmap -sS -O <ip>
```

- Output formatting

```shell
nmap -sS -oN <ip> # normal, same is to console
nmap -sS -oG <ip> # grepabble
nmap -sS -oX <ip> #xml
```

## Custom scripts - NSE

- scripts located in /usr/share/nmap/scripts
- use --script to define what you want to use
- by default we use default, defined via -sC too
- more is possible: auth, broadcast, brute, default, discovery, dos, exploit, external, fuzzer, intrusive, malware, safe, version, vuln
- run custom script

```shell
nmap --script "<name>" <ip>
```
