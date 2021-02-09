---
tags: [Python]
title: 'if, else, elif, and User input()'
created: '2021-02-09T20:14:13.233Z'
modified: '2021-02-09T20:15:10.415Z'
---

# `if`, `else`, `elif`, and User `input()`

``` python
# If
name = 'Alice'
if name =='Alice':
    print('Where\'s my money?')
print('Done')

# Else
password = 'swordfish'
if password == 'swordsfish':
    print('Access granted.')
else:
    print('I\'m calling the cops.')

# Elif
name = 'Bob'
age = 3000
if name == ('Alice'):
    print('Hi Alice!')
elif age < 12:
    print('You are not Alice, kiddo!')
elif age > 2000:
    print('Unlike you, Alice is not an undead, immortal vampire')
elif age > 100:
    print('You are not Alice, granny!')

# User input
name = input()
if name:
    print('Cheers for entering a name, ' + name + '!')
else:
    print('No name, eh?')
```
