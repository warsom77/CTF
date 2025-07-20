# philtered – Web – Beginner

**URL:**  
https://web-philtered-0a2005e5b9bf.2025.ductf.net/

---

## Deskripsi

> Can you phigure this one out?

Kita diberikan source code aplikasi web PHP sederhana. Tujuan dari challenge ini adalah mendapatkan flag yang berada di file `flag.php`.

---

## Analisis Source Code

File utama `index.php` menjalankan kode berikut:

```
$loader = new FileLoader(); 
$loader->assign_props($_GET);
```
Hal ini berarti semua input dari URL (melalui $_GET) akan digunakan untuk mengatur properti pada objek FileLoader.
```
public function contains_blacklisted_term($value) {
    if (!$this->allow_unsafe) {
        foreach ($this->blacklist as $term) {
            if (stripos($value, $term) !== false) {
                return true;    
            }
        }
    }
    return false;
}
```
Blacklist hanya aktif jika allow_unsafe == false. Jika kita menyetel allow_unsafe = 1, maka fungsi ini akan dilewati dan tidak ada filter terhadap input seperti ../, flag, dll.
```
class Config {
    public $path = 'information.txt';
    public $data_folder = 'data/';
}
```
Properti path dan data_folder menentukan file yang akan dibaca oleh fungsi load() berikut:
```
public function load() {
    return file_get_contents($this->config->data_folder . $this->config->path);
}
```

---

## Teknik Eksploitasi
### 1. Bypass Blacklist
- Set allow_unsafe=1 untuk melewati pengecekan blacklist.
### 2. Manipulasi Config
- Dengan parameter config[path]=../flag.php akan mengubah isi $loader->config->path menjadi '../flag.php';
- Kemudian fungsi load() akan menjalankan file_get_contents('data/../flag.php'); Karena data/../flag.php secara teknis adalah path valid menuju file flag.php, maka file tersebut berhasil dibaca.

### Payload Final
https://web-philtered-0a2005e5b9bf.2025.ductf.net/index.php?allow_unsafe=1&config[path]=../flag.php

### Flag
Buka URL di atas, lalu lihat View Page Source di browser.

> DUCTF{h0w_d0_y0u_l1k3_y0ur_ph1lters?}