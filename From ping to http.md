# From ping to http
## Setting up
Enne käivitamist käsud
```
sudo apt-get update (&& sudo apt-get upgrade)
sudo apt-get install netcat-openbsd tcpdump traceroute mtr iputils-ping lsof
```
## Ping vs HTTP
- Ping
  - Echo request to an operating system
- HTTP
  - HTTP recuest to a web server
### Writing your own HTTP
- for example to wikipedia

``printf 'HEAD / HTTP/1.1\r\nHost: en.wikipedia.org\r\n\r\n' | nc en.wikipedia.org 80``

| in UNIX means
- Take the output of this program | and feed it in as the input of that program
    - `| nc en.wikipedia.org 80` - nc connects to host
    - en.wikipedia.org...| - what website we want from that host
      
## printf & netcat
- printf
  - doesn't know anything about the network
  - for printing formated strings

printf turns `\n` into linebreak, echo doesnt
- nc
  - doesn't know about forming http recuests
  - manually talking to internet services
  - connecting to servers and acting like a server

## Listening and connecting
`man nc` to open nc manual

`nc -l 3456` to listen on a port

`nc localhost 3456` to open port
- only one program can listen at a time

``sudo lsof -i`` to see programs that are listening

(ctrl D) to end session
  - (ctrl C) worked in my case

Note: if you receive an error `nc: getaddrinfo: nodename nor servname provided, or not known` , you can add ``127.0.0.1 localhost`` to ``hosts`` to solve the issue.
### Be a web server
``printf 'HTTP/1.1 302 Moved\r\nLocation: https://www.eff.org/' | nc -l 2345``

Then point your web browser at the server's IP address
- You will need to use the IP address of your Linux server in the URL that you put into your browser.

## ERRORS

