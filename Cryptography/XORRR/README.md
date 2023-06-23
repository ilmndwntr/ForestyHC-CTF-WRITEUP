# Xorrr
Still remember last night?

```
Encrypt: 355c111740002628673f08580617432b36056c14425d072d6c0c6f196c10006c111745472d185a1b1f563c4055156e590704
```

Format Flag: ForestyCTF{flag}
## Solution
Di beri sebuah encryptor nya

```py
#!/usr/bin/python3

FLAG = b"ForestyCTF{XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX}"
KEY = b"??????????"

assert len(KEY) == 10

def encrypt(plaintext : bytes, key : bytes) -> bytes:
    ciphertext = []
    for i in range(len(plaintext)):
        ciphertext.append(plaintext[i] ^ key[i % len(key)])
    return bytes(ciphertext).hex()

encrypted_flag = encrypt(FLAG, KEY) 
print(encrypted_flag)
```

bisa di liat KEY nya tidak kasih tau jadi saya harus mencari key nya, saya mengingat materi Cryptography yang di bawakan oleh kak Nuril. Jadi saya membuat sebuah codingan untuk mencari KEY nya

**Code**

```py
from pwn import xor

cipher= "355c111740002628673f08580617432b36056c14425d072d6c0c6f196c10006c111745472d185a1b1f563c4055156e590704"
cipher = bytes.fromhex(cipher)

knownFlag = b"ForestyCTF{flag}"
knownKey = b""
print(xor(cipher,knownFlag))
```

untuk variabel knowFlag itu kita sudah mengetahui Format Flag nya seperti apa untuk Format nya adalah ```ForestyCTF{```

**The Command**

```
┌──(k1ra㉿ilmndwntr)-[/mnt/c/Users/ASUS/Downloads]
└─$ python3 encryptor.py
b's3cr3t_k3ys>jv$Vpj\x1eq1)~n8J\x14\x7f\x00qg\x11Wx7"^l#XK\x10G&9t\t$Ak'
```

lalu di ketahui juga panjang dari KEY nya adalah 10

```assert len(KEY) == 10```

jadi kita ambil 10 kata dari depan, jadi KEY nya adalah ```s3cr3t_k3y```

langsung saja kita masukan KEY nya ke dalam kodingan kita tadi

```py
from pwn import xor

cipher= "355c111740002628673f08580617432b36056c14425d072d6c0c6f196c10006c111745472d185a1b1f563c4055156e590704"
cipher = bytes.fromhex(cipher)

knownFlag = b"ForestyCTF{flag}"
knownKey = b"s3cr3t_k3y"
print(xor(cipher,knownKey))
```

**The Command**

```
┌──(k1ra㉿ilmndwntr)-[/mnt/c/Users/ASUS/Downloads]
└─$ python3 encryptor.py
b'ForestyCTF{keep_in_m1nd__x0r_is_rev3rsible_2fa124}'
```

```FLAG: ForestyCTF{keep_in_m1nd__x0r_is_rev3rsible_2fa124}```

![Screenshot](https://media.tenor.com/kfKIq2AP4NoAAAAM/mcdonalds-grimace.gif)
