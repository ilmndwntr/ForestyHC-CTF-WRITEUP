# Rawwrr
Stegosaurus is a genus of herbivorous, four-legged, armored dinosaur from the Late Jurassic, characterized by the distinctive kite-shaped upright plates along their backs and spikes on their tails. Did you know, the last Stegosaurus is hiding somewhere, his name is Amo Eno Stee, he has the number 256 on his shoulder.

there are many tools to extract hidden message, try to Open another Stego tools

## Solution
Setelah saya cerna dari hint yang dikasih saya langsung searching tentang OpenStego ternyata ada, lalu saya memakai tools nya

![Screenshot](https://raw.githubusercontent.com/ilmndwntr/ForestyHC-CTF-WRITEUP/main/Forensic/Rawwrr/ss.png)

setelah di extract kita di kasih output berupa file ```secret```, setelah saya coba buka file bertype bytes 

```
k1ra@ilmndwntr:~/ForestyCTF2023/Forensic/Rawrrr/stegbuka$ cat secret
\x57\x68\x79\x20\x61\x72\x65\x20\x79\x6f\x75\x20\x6c\x6f\x6f\x6b\x69\x6e\x67\x20\x66\x6f\x72\x3f\x0a\x69\x73\x20\x74\x68\x65\x72\x65\x20\x73\x6f\x6d\x65\x74\x68\x69\x6e\x67\x20\x73\x70\x65\x63\x69\x61\x6c\x20\x69\x6e\x20\x68\x65\x72\x65\x3f\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x66\x69\x6e\x65\x2e\x20\x69\x74\x27\x73\x20\x66\x6f\x72\x20\x79\x6f\x75\x0a\x52\x6d\x39\x79\x5a\x58\x4e\x30\x65\x55\x68\x44\x65\x32\x70\x31\x4e\x58\x52\x30\x64\x46\x39\x69\x4e\x44\x56\x70\x51\x30\x4e\x66\x63\x33\x51\x7a\x5a\x7a\x42\x39
```

lalu saya melakukan decode dari bytes menjadi string

```
k1ra@ilmndwntr:~/ForestyCTF2023/Forensic/Rawrrr/stegbuka$ python3
Python 3.10.6 (main, May 29 2023, 11:10:38) [GCC 11.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print(b"\x20\x61\x72\x65\x20\x79\x6f\x75\x20\x6c\x6f\x6f\x6b\x69\x6e\x67\x20\x66\x6f\x72\x3f\x0a\x69\x73\x20\x74\x68\x65\x72\x65\x20\x73\x6f\x6d\x65\x74\x68\x69\x6e\x67\x20\x73\x70\x65\x63\x69\x61\x6c\x20\x69\x6e\x20\x68\x65\x72\x65\x3f\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x2e\x0a\x66\x69\x6e\x65\x2e\x20\x69\x74\x27\x73\x20\x66\x6f\x72\x20\x79\x6f\x75\x0a\x52\x6d\x39\x79\x5a\x58\x4e\x30\x65\x55\x68\x44\x65\x32\x70\x31\x4e\x58\x52\x30\x64\x46\x39\x69\x4e\x44\x56\x70\x51\x30\x4e\x66\x63\x33\x51\x7a\x5a\x7a\x42\x39".decode("utf-8"))
 are you looking for?
is there something special in here?
.
.
.
.
.
.
.
.
.
.
.
.
.
fine. it's for you
Rm9yZXN0eUhDe2p1NXR0dF9iNDVpQ0Nfc3QzZzB9
```
AND BOOM KITA BERHASIL DAPET MESSAGE NTA, eitts tapi ada apa nih kok ga ada **FLAG**nya ohh ternyata kita harus mendecode lagi ```Rm9yZXN0eUhDe2p1NXR0dF9iNDVpQ0Nfc3QzZzB9``` dia tipe nya base64 langsung aja kita decode

![Screenshot](https://media.tenor.com/x8v1oNUOmg4AAAAd/rickroll-roll.gif)

```
import base64
coded_string = 'Rm9yZXN0eUhDe2p1NXR0dF9iNDVpQ0Nfc3QzZzB9'
x = base64.b64decode(coded_string)

print(x)
```

```
k1ra@ilmndwntr:~/ForestyCTF2023/Forensic/Rawrrr/stegbuka$ python3 base64decode.py
b'ForestyHC{ju5ttt_b45iCC_st3g0}'
```

and BOOM kita mendapatkan FLAG nya

```FLAG: ForestyHC{ju5ttt_b45iCC_st3g0}```

![Screenshot](https://media.tenor.com/qzc9bkg5RNcAAAAC/but-why-tho.gif)

easy bukan?
