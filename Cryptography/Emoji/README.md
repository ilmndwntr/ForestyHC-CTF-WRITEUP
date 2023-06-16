# Emoji
My friend sent a message that contains a lot of emojis. He says that there is a secret message behind it.

Can you find the message behind it?

Format Flag: ```ForestyHC{DECRYPTEDMESSAGE}```
## Solution
Di berikan sebuah file berisikan ```😈 😒 😓 😇 😈 😒 😑 😄 😀 😋 😋 😘 😂 😑 😘 😏 😓 😎 😂 😇 😀 😋 😋```

lalu di berikan sebuah codingan python sebagai HINT nya

```
import string

def emojiCrypt(plainText):
    emojis = []
    for c in plainText:
        if c not in string.ascii_uppercase:
            emojis.append(c)
        else:
            code = string.ascii_uppercase.index(c) + 0x1F600
            emojis.append(chr(code))
    return ' '.join(emojis)
```

lalu setelah di pahami dalam codingan python nya terdapat function emojiCrypt untuk mengambil pesan teks biasa sebagai input dan mengganti setiap huruf besar dalam pesan dengan emoji yang sesuai, secara khusus menggunakan fungsi ord() untuk mendapatkan titik kode unicode dari emoji yang sesuai untuk setiap huruf, yang di hitung sebagai ```0x1F600``` di tambah indeks huruf dalam alfabet huruf besar.

untuk mendekripsi kan pesan ini, saya perlu membalikan proses, saya perlu mengekstrak huruf dari emoji lalu mengonversi setiap huruf kembali ke karakter teks biasa yang sesuai

berikut codingan python:

```
import string

def emojiDecrypt(cipherText):
    emojis = cipherText.split()
    plainText = []
    for emoji in emojis:
        code_point = ord(emoji)
        if 0x1F600 <= code_point <= 0x1F64F:
            index = code_point - 0x1F600
            if 0 <= index < 26:
                plainText.append(string.ascii_uppercase[index])
        elif 0x1F680 <= code_point <= 0x1F6FF:
            index = code_point - 0x1F680 + 26
            if 26 <= index < 52:
                plainText.append(string.ascii_uppercase[index])
    return ''.join(plainText)

cipherText = "😈 😒 😓 😇 😈 😒 😑 😄 😀 😋 😋 😘 😂 😑 😘 😏 😓 😎 😂 😇 😀 😋 😋"
plainText = emojiDecrypt(cipherText)
print(plainText)
```

**pov my brain now**:

![Screenshot](https://media.tenor.com/fF0N2mmkW-QAAAAC/mind-blown.gif)
