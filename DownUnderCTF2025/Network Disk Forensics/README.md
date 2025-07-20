# Network Disk Forensics – Misc – Beginner

**Remote:**  
nc chal.2025.ductf.net 30016

---

## Deskripsi

> Nobody likes having to download large disk images for CTF challenges so this time we're giving you a disk over the network!

Challenge ini membangun filesystem Ext4 virtual secara dinamis dan menyisipkan flag dalam sebuah file gambar JPEG. Filesystem ini lalu disajikan melalui NBD (Network Block Device).
### Tujuannya
1. Terhubung ke NBD server dan mendapatkan device virtual.
2. Mount filesystem virtual Ext4 dari device tersebut.
3. Cari dan buka file flag.jpg untuk memperoleh flag.

---

## Analisis Source Code

1. generateTextPNG()
   - Fungsi untuk membuat gambar JPEG dengan teks tertentu (termasuk flag).
2. generateFileSystem()
   - Membuat direktori bersarang.
   - Membuat dummy file .txt dan .jpg pada setiap direktori.
   - Flag disisipkan di salah satu bottom directory secara acak sebagai .jpg.
   - Juga dibuat symlink flag.jpg di root yang menunjuk ke flag asli.
3. filesystemToExt4()
   - Mengubah struktur direktori ke format Ext4 virtual di memory.

---

## Langkah:
### 1. Koneksi ke NBD Server
```commandline
sudo modprobe nbd
sudo nbd-client -name root chal.2025.ductf.net 30016 /dev/nbd0
```
### 2. Mount Filesystem
```commandline
mkdir mnt
sudo mount /dev/nbd0 mnt
```
### 3. Baca flag.jpg
```commandline
feh mnt/flag.jpg
```

### Flag

> DUCTF{now_you_know_how_to_use_nbd_4y742rr2}