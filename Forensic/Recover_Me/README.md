# Recover Me
Probsetter creates a flag in the form of an image file, and saved it on Google Docs as an URL. But he forgot to restrict his document access. Can you find the file? 

```https://docs.google.com/document/d/1QhzkIt2TESJPAuyP_iQSxft6d7D9crCh7fwzxRUJsCQ/edit?usp=sharing```

```Put the flag into proper format : ForestyHC{}```

## Solution
Diberikan sebuah URL Google Docs, ternyata hanya sebuah text biasa saja, tapi cek dulu History Versi nya, ternyata ada sebuah link

```https://drive.proton.me/urls/1JWDW5RCCG#TaWxbUKYWE0k```

setelah di download ternyata berupa file ```.png``` saat mau di bukan ternyata file tersebut rusak, setelah melakukan pengecekan ternyata format di dalam file nya salah.

```
k1ra@ilmndwntr:~/ForestyCTF2023/Forensic/Recover_Me$ hexdump -C Bendera.png | head
00000000  89 4c 4f 4c 0d 0a 1a 0a  00 00 00 0d 49 48 42 52  |.LOL........IHBR|
00000010  00 00 08 70 00 00 09 60  08 02 00 00 00 65 0f c5  |...p...`.....e..|
00000020  11 00 00 00 09 70 48 59  73 00 00 0e f3 00 00 0e  |.....pHYs.......|
00000030  f3 01 1c 53 99 3a 00 00  00 11 74 45 58 74 54 69  |...S.:....tEXtTi|
00000040  74 6c 65 00 50 44 46 20  43 72 65 61 74 6f 72 41  |tle.PDF CreatorA|
00000050  5e bc 28 00 00 00 13 74  45 58 74 41 75 74 68 6f  |^.(....tEXtAutho|
00000060  72 00 50 44 46 20 54 6f  6f 6c 73 20 41 47 1b cf  |r.PDF Tools AG..|
00000070  77 30 00 00 00 2d 7a 54  58 74 44 65 73 63 72 69  |w0...-zTXtDescri|
00000080  70 74 69 6f 6e 00 00 08  99 cb 28 29 29 b0 d2 d7  |ption.....())...|
00000090  2f 2f 2f d7 2b 48 49 d3  2d c9 cf cf 29 d6 4b ce  |///.+HI.-...).K.|
```

terdapat **LOL** yang seharus nya **PNG** dan **IHBR** yang seharus nya **IHDR**, langsung saja kita edit menggunakan Hex Editor

![Screenshot](https://raw.githubusercontent.com/ilmndwntr/ForestyHC-CTF-WRITEUP/main/Forensic/Flagzz/ss1.png)

setelah melakukan perubahan saat nya kita buka gambar nya and BOM ternyata itu adalah FLAG nya

![Screenshot](https://raw.githubusercontent.com/ilmndwntr/ForestyHC-CTF-WRITEUP/main/Forensic/Flagzz/ss2.png)

ez bukan?

![Screenshot](https://media.tenor.com/cwoN93BINOMAAAAC/so-good-wink.gif)

```FLAG: ForestyHC{f0rensh33sh_isnt_th4t_h4rdzz_h0h0_ef233c}```