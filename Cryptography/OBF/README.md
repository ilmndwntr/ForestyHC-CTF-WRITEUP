# OFB
Oh no! Someone just sent me some suspicious file, and I accidentally opened it. Suddenly, all my files are encrypted. Fortunately, I have backed up one of the encrypted files and found this when I tried to reverse the file.

```py
def encrypt(plaintext):
    cipher = AES.new(KEY, AES.MODE_OFB, IV)
    ciphertext = cipher.encrypt(pad(plaintext, AES.block_size))
    return ciphertext
```

## Solution
- [x] Melakukan XOR antara file ```banner.png.enc``` dan ```banner.png```, melakukan XOR ini untuk mendapatkan **keystream** nya
- [x] Melakukan XOR antara ```flag.png.enc``` dengan keystream yang sudah kita dapatkan
- [x] Output nya flag.png

```FLAG: ForestyHC{the_real_malware_never_use_OFB_1a42fa}```

![Screenshot](https://media1.giphy.com/media/s2qXK8wAvkHTO/giphy.gif)
