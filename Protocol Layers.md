# Protocol Layers
- the Protocol Stack
  - application - HTTP / SSH / NTP
  - transport - TCP / UDP
  - internet - IP
  - hardware - Ethernet / Wifi
## tcpdump
### Ping & DNS
`ping -c3 8.8.8.8` & `sudo tcpdump -n host 8.8.8.8`

to see all the DNS recuest your device sends `sudo tcpdump -n port 53`
- DNS uses port 53
### HTTP
to look at the pacets your device uses to talk to a web server `sudo tcpdump -n port 80`

& `printf 'HEAD / HTTP/1.1\r\nHost: example.net\r\n\r\n' | nc example.net 80`
#### analizing
``` 
sudo tcpdump -n port 80
13:47:33.147534 IP 172.17.0.4.41198 > 157.240.20.35.80: Flags [S], seq 4012631139, win 64240, 
(options [mss 1460,sackOK,TS val 2688967179 ecr 0,nop,wscale 7],) length 0
13:47:33.156070 IP 157.240.20.35.80 > 172.17.0.4.41198: Flags [S.], seq 438743794, ack 4012631140, win 65535,
(options [mss 1392,sackOK,TS val 2423284953 ecr 2688967179,nop,wscale 8],) length 0
13:47:33.156107 IP 172.17.0.4.41198 > 157.240.20.35.80: Flags [.], ack 1, win 502,
(options [nop,nop,TS val 2688967187 ecr 2423284953],) length 0
{ 13:47:33.156195 IP 172.17.0.4.41198 > 157.240.20.35.80: Flags [P.], seq 1:40, ack 1, win 502,
(options [nop,nop,TS val 2688967188 ecr 2423284953],) length 39: HTTP: HEAD / HTTP/1.1 } - EXACTLY REPRESENTS THE TRANSMITION OF THE http RECUEST FROM OUR CLIENT TO THE FACEBOOK.COM SERVER
13:47:33.163953 IP 157.240.20.35.80 > 172.17.0.4.41198: Flags [.], ack 40, win 256,
(options [nop,nop,TS val 2423284961 ecr 2688967188],) length 0
{ 13:47:33.164056 IP 157.240.20.35.80 > 172.17.0.4.41198: Flags [P.], seq 1:197, ack 40, win 256,
(options [nop,nop,TS val 2423284962 ecr 2688967188],) length 196: HTTP: HTTP/1.1 301 Moved Permanently } - REPRESENTS THE RESPONCE FROM THE SERVER TO THE CLIENT
13:47:33.164066 IP 172.17.0.4.41198 > 157.240.20.35.80: Flags [.], ack 197, win 501,
(options [nop,nop,TS val 2688967195 ecr 2423284962],) length 0
^C
```
## TCP
### flags
The Flags field in tcpdump tells you which flags, or control bits, are set on each TCP packet.

What is a flag?
- In low-level computer languages, a flag is a Boolean value — a true or false value — that is stored in memory as a single bit. If a flag bit is 1, we say the flag is set. If the flag bit is 0, the flag is cleared (or unset).

Usually, flags come in groups, each of which can be set or cleared.

## keep in mind
timeout on recuests
failiures can happen
design your error handling with care
