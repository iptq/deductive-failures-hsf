# 100 What's Good?

> http://54.152.176.49

Looking at the source code of the site, there's nothing that really stands out, other than the skeleton playing a trumpet and the link to [/whereyouat](http://54.152.176.49/whereyouat).

```bash
{ ~ }  » nc 54.152.176.49 80
GET /whereyouat HTTP/1.0

HTTP/1.0 200 OK
Content-Type: text/html; charset=utf-8
Content-Length: 9
The-Flag-:3: flag{html_response_headers_hold_the_secrets_to_everything}
Server: Werkzeug/0.10.4 Python/2.7.6
Date: Fri, 09 Oct 2015 02:29:51 GMT

Doot Doot
```

Performing a simple `GET` on `/whereyouat` using netcat reveals that the flag is in the header.

## Flag

`flag{html_response_headers_hold_the_secrets_to_everything}`