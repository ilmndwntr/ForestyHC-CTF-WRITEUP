# Flagzz
My friend sent me a file, but I can't open it with the audio player. He says the file is too noisy, and wants you to check it

## Solution
Diberikan sebuah file audio berformat ```.wav```, setelah saya menggunakan tools Audacity dan melihat spectrogram nya terdapat message tersembunyi yaitu ```bit.ly/flagzz``` setelah saya membuka link tersebut terdownload sebuah file **WireShark** 

![Screenshot](https://raw.githubusercontent.com/ilmndwntr/ForestyHC-CTF-WRITEUP/main/Forensic/Flagzz/ss1.png)

dan setelah di cek satu persatu nomor paket nya, ternyata ada sebuah request post pada url ```/figlet``` setelah di lihat isi paket tersebut terdapat object yang di tunjukan sebuah string yang ternyata itu adalah FLAG nya

![Screenshot](https://raw.githubusercontent.com/ilmndwntr/ForestyHC-CTF-WRITEUP/main/Forensic/Flagzz/ss2.png)

ez bukan?

![Screenshot](https://media.tenor.com/-E6edZFWFXwAAAAC/cool-duck-duck.gif)

```FLAG: ForestyHC{h3h3_u_f0und_m3_btw_infokan_libur_smt_a12e47}```