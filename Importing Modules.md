---
tags: [Python]
title: Importing Modules
created: '2021-02-09T20:04:33.611Z'
modified: '2021-02-09T20:05:00.757Z'
---

# Importing Modules

``` python
# import random module so we can use randint()
import random
print(random.randint(1, 10))

# import all from random / avoid dot syntax
from random import *
print (randint(1, 100))

# import 3rd party module, pyperclip:
# > cd C:\Users\USER\AppData\Local\Programs\Python\Python39\Scripts>
# > ./pip install pyperclip
# pip will not be installed automatically on linux
import pyperclip
pyperclip.copy('hello world!')
print(pyperclip.paste())
```
