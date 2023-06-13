# Sanity Check
Disini kita diberikan sebuah Ciphertext: 466f726573747948437b77656c636f6d655f746f5f6861636b65725f636c6173735f666f72657374795f3539366537377d0a

## Solution
Untuk solusi nya adalah pertama saya melakukan Cipher Identifier and Analyzer di website
https://www.boxentriq.com/code-breaking/cipher-identifier
![Screenshot from 2023-06-14 01-02-23](https://raw.githubusercontent.com/ilmndwntr/ForestyHC-CTF-WRITEUP/main/Miscellaneous/Sanity%20Check/identifier.png)
setelah melakukan identifier and Analyzer ternyata Ciphertext tersebut adalah Hex
![Screenshot from 2023-06-14 01-02-23](https://raw.githubusercontent.com/ilmndwntr/ForestyHC-CTF-WRITEUP/main/Miscellaneous/Sanity%20Check/decode.png)
lalu saya melakukan decode hexnya dan hasil nya adalah ForestyHC{welcome_to_hacker_class_foresty_596e77}
