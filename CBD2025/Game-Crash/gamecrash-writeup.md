# Game Crash

**Deskripsi**  
> My favorite game keeps crashing :(  
> Password File : `63dd90b95f1e8e80b312619fb72d75a852d7ffddb4bd2c8b3cc119b3f27ba9ea`  
> Author: Cyrus  

---

## Langkah Penyelesaian

1. **Ekstraksi File**
   - Diberikan file `crash.7z`.  
   - File tersebut dilindungi password. Password ada di deskripsi soal.  
   - Setelah diekstrak, diperoleh file dump: `crash.dmp`.

2. **Analisis File Dump**
   - Untuk melihat isi file, jalankan perintah:
     ```bash
     strings crash.dmp | less
     ```
   - Author memberikan hint bahwa **flag terbagi menjadi 3 part**, dan setiap part di-*encode* menggunakan metode yang sama.  
   - Dari hasil `strings`, terlihat ada banyak variabel dengan value dalam format **base64, hex, dan binary**.

3. **Filter Data yang Mencurigakan**
   - Untuk memudahkan pencarian, gunakan perintah berikut:
     ```bash
     strings crash.dmp | grep -En '[A-Za-z0-9_+]+=[A-Za-z0-9+/=]+'
     ```
   - Perintah ini menampilkan string yang berbentuk `key=value`, dan ternyata berisi potongan flag.

---

## Analisis Potongan Flag

### Part 1
```
SESSION_RULES=01010000010011110101000101111011011110100110110001011111
```
- Nilai berupa **biner**. Jika di-decode → `ROT13` menghasilkan:  
```
POQ{zl_ → ROT13 → CBD{my_
```

### Part 2
```
+ld=ZzRt → base64 decode → g4m
+pp=M19r → base64 decode → 3_k
+xn=MzNwXw== → base64 decode → 33p_
```

### Part 3
```
MAP_AZ=63723473 → hex decode → cr4s
TLS_RP=68316e67 → hex decode → h1ng
INI_QF=5f68336c → hex decode → _h3l
UXP_HK=705f6d33 → hex decode → p_m3
IOX_ML=5f706c7a → hex decode → _plz
KCFG_VE=5f66676d → hex decode → _fgm
SEED_Z9=32397a7d → hex decode → 29z}
```

---

## Rekonstruksi Flag
Menggabungkan semua hasil decoding:

```
Part 1: CBD{my_
Part 2: g4m3_k33p_
Part 3: cr4sh1ng_h3lp_m3_plz_fgm29z}
```

**Final Flag:**
>CBD {my_g4m3_k33p_cr4sh1ng_h3lp_m3_plz_fgm29z}

---

Solvenya setelah kumpul write-up, jadi tidak sempat *submit* di scoreboard 😅.  