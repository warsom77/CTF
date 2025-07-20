# our-lonely-dog – Misc – Beginner

---

## Deskripsi

> e-dog has been alone in the downunderctf.com email server for so long, please yeet him an email of some of your pets to keep him company, he might even share his favourite toy with you.  
>
> He has a knack for hiding things one layer deeper than you would expect.

---

## Analisis

Dari deskripsi, kita diminta untuk mengirim email ke `e-dog@downunderctf.com`
dengan melampirkan **foto hewan peliharaan**.

Langkah-langkah:

1. Mengirim email ke `e-dog@downunderctf.com` dengan **lampiran gambar hewan peliharaan**.
2. Setelah beberapa saat, menerima **balasan email dari e-dog**.
3. Namun, isi email tersebut tampak biasa saja dan **tidak mengandung flag secara eksplisit**.
4. Berdasarkan petunjuk:
   > _"He has a knack for hiding things one layer deeper than you would expect."_
   
   Kemungkinan flag disembunyikan di bagian yang tidak umum dari email.

---

## Solusi

Membuka email balasan menggunakan fitur **“show original”** atau **“view raw source”** (tergantung layanan email yang digunakan).
Di sana ditemukan **custom email header** bernama:
`X-FLAG`

### Flag

> DUCTF{g00d-luCk-G3tT1nG-ThR0uGh-Al1s-Th3-eM41Ls}