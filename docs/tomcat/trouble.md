

* ICMP PING을 통해 host 확인  
```
$ ping 206.189.80.229
```

* port까지 추가하여 application이 **OPEN**되었는지 확인  
```
$ nmap -p 8080 206.189.80.229

Starting Nmap 7.60 ( https://nmap.org ) at 2020-06-29 02:35 KST
Nmap scan report for 206.189.80.229
Host is up (0.25s latency).

PORT     STATE SERVICE
8080/tcp open  http-proxy

Nmap done: 1 IP address (1 host up) scanned in 0.91 seconds
```

