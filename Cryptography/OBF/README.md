# OFB
Oh no! Someone just sent me some suspicious file, and I accidentally opened it. Suddenly, all my files are encrypted. Fortunately, I have backed up one of the encrypted files and found this when I tried to reverse the file.

```py
def encrypt(plaintext):
    cipher = AES.new(KEY, AES.MODE_OFB, IV)
    ciphertext = cipher.encrypt(pad(plaintext, AES.block_size))
    return ciphertext
```

## Solution
Kalian bisa gunakan tool di bawah ini:

```py
def xor_bytes(a, b):
    return bytes(x ^ y for x, y in zip(a, b))

def get_flag(keystream):
    with open('flag.png.enc', 'rb') as file_enc:
        enc_data = file_enc.read()
        flag_data = xor_bytes(enc_data, keystream)
        with open('flag.png', 'wb') as file_flag:
            file_flag.write(flag_data)

def get_keystream():
    with open('banner.png.enc', 'rb') as file_enc, open('banner.png', 'rb') as file_plain:
        enc_data = file_enc.read()
        plain_data = file_plain.read()
        keystream = xor_bytes(enc_data, plain_data)
        return keystream

# Mendapatkan keystream
keystream = get_keystream()

# Mendapatkan flag
print(get_flag(keystream))
```

- [x] Melakukan XOR antara file ```banner.png.enc``` dan ```banner.png```, melakukan XOR ini untuk mendapatkan **keystream** nya
- [x] Melakukan XOR antara ```flag.png.enc``` dengan keystream yang sudah kita dapatkan
- [x] Output nya flag.png

```FLAG: ForestyHC{the_real_malware_never_use_OFB_1a42fa}```

![Screenshot](https://media1.giphy.com/media/s2qXK8wAvkHTO/giphy.gif)
