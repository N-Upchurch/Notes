---
tags: [Python]
title: while loops
created: '2021-02-09T20:13:16.664Z'
modified: '2021-02-09T20:13:54.383Z'
---

# `while` loops

``` python
# Example 1
spam = 0
while spam < 5:
    print('hello world!')
    spam = spam + 1

# Example 2
name = ''
while True:
    print("Please type your name")
    name = input()
    if name == 'your name':
        break
print('Thanks')
```
