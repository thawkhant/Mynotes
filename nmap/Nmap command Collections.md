

nmap 10.0.0.1 -sV 20,8080   

nmap -p 25 10.0.0.1 -sV -sC    => version details ko pya pay dal

nmap 10.0.0.1 -sV -p 1-100    => from start 1 to 100

nmap --script=smb-enum-shares 10.0.0.1 -sV -p 445      => smb enum loke dar 

nmap --script=smb-enum-users 10.0.0.1 -sV -p 445  

nmap 10.0.1.1 -oN results.txt   => result htal ko htat dar

nmap 10.0.0.1 -p- -oN all.txt   => All ports ko check dar  **

sudo nmap 10.0.0.1 --top-ports 100    => commoly use de top ports ko check dar

nmap 10.0.0.1 -p1-65535     => all port ko check dar

nmap 10.0.0.1 -p 1-1000     

sudo nmap 10.0.0.1 -O    => KERNEL KO check dar => OS ko check dar