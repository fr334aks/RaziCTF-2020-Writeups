## Challenge Description:

I gave the flag to a friend of mine to protect it, she likes riddles and apparently has a bad temper. Go say hi: nc sphinx.razictf.ir 1379

When you connect to the challenge host. You get a base64 encoded image and you need to answer the question with the position of the shape 
within a short period of time or the connection would time out.

I used this script to get the images and manually answered the questions.

```py

#!/usr/bin/env python3
import base64
from pwn import *
import os
host = "sphinx.razictf.ir"
port = 1379
io = remote(host,port)
io.recv(1024)
io.sendline('yes')

for i in range(1,21):
    encoded = io.recvuntil('? ')
    enc_image = encoded.decode().split('\n')[0]
    question = encoded.decode().split('\n')[1]
    f = open('image1.png','wb')
    f.write(base64.b64decode(enc_image))
    f.close()
#os.system('eog image1.png &')
    print(str(i) + " " +question)
    io.sendline(input('> '))
    #print(io.recvuntil('? '))
print(io.recv().decode())

```
