# 🕵️ ExchangeGhost - Writeup

## 📌 Deskripsi
**Scenario:**  
Nusantara Energy is preparing internal fund disbursement for regional Q3 operations. A sequence of email communications occurs between internal stakeholders and an external consultant from Kensei Corporation.

- **Difficulty:** Easy  
- **File Diberikan:** `ExchangeGhost.zip` berisi:
  - `mail-005.eml`, `mail-009.eml`, `mail-012.eml`, `mail-020.eml`
  - `audit.csv`

File tersebut digunakan untuk menjawab beberapa pertanyaan investigasi forensik di bawah ini.

---

## 🔍 Pertanyaan & Jawaban

### 1. Identify the sender's email address that initiated the phishing attempt  
**Format:** `email@domain.ltd`

📂 **Analisis:**
- Pada file `mail-020.eml`, terdapat email yang meminta korban untuk mengakses sebuah link.
- Email pengirim teridentifikasi sebagai:

✅ **Jawaban:**  
> yuki.matsuda@kenseicorp.jp

---

### 2. What type of compromise is this?  
**Format:** Text

📂 **Analisis:**
- Dari pola komunikasi & aktivitas yang terjadi, insiden ini termasuk kategori **phishing berbasis manipulasi email bisnis**.

✅ **Jawaban:**  
> Business Email Compromise

---

### 3. List the two public IP addresses used by the threat actor to perform unauthorized access  
**Format:** `x.x.x.x,x.x.x.x`

📂 **Analisis:**
- Pada `audit.csv`, UserId `sari.wulandari@nusantaraenergy.co.id` digunakan oleh attacker.  
- Terdapat operation `New-InboxRule` dengan IP address asing.  
- Dua IP berbeda yang mencurigakan adalah:

✅ **Jawaban:**  
> 198.51.100.23,203.0.113.45


---

### 4. Determine the financial institution that received the fund transfer  
**Format:** Text

📂 **Analisis:**
- Pada `mail-005.eml`, ditemukan detail reimbursement:

```
Full Name: Ratna Siregar
Employee Code: NSR0492
Requested Amount: IDR 75,000,000
Purpose: Regional training expense reimbursement
Submission Date: 02/07/2025
SWIFT/BIC: CITIUS33
Bank Account: 032101009823
```

- SWIFT code `CITIUS33` merujuk pada **CITIBANK N.A.**

✅ **Jawaban:**  
> CITIBANK N.A.

---

### 5. Specify the name of the mailbox folder that was created by the attacker during the compromise  
**Format:** Text

📂 **Analisis:**
- Pada log `audit.csv`, operation `FolderCreated` menunjukkan adanya folder baru.  
- Nama folder tersebut adalah `client_archive`.

✅ **Jawaban:**  
> client_archive

---

### 6. What keyword was targeted by the attacker’s first inbox rule for email deletion, either in the subject line or message body?  
**Format:** Text

📂 **Analisis:**
- Pada `New-InboxRule` dengan UserId `sari.wulandari@nusantaraenergy.co.id`, parameter `SubjectContainsWords` memiliki value:  
```
jakarta fund request
```

✅ **Jawaban:**  
> jakarta fund request

---

### 7. What is the Outlook rule name created by the attacker?  
**Format:** Text

📂 **Analisis:**
- Pada log `New-InboxRule`, parameter `Name` menunjukkan nilai berikut:
```
Default Rule 1
```

✅ **Jawaban:**  
> Default Rule 1

---

## 📂 Bukti Log (Potongan)
Contoh record dari `audit.csv` yang menunjukkan pembuatan inbox rule:

```json
{
  "Operation": "New-InboxRule",
  "UserId": "sari.wulandari@nusantaraenergy.co.id",
  "ClientIP": "203.0.113.45:52445",
  "Parameters": [
    {"Name": "SubjectContainsWords", "Value": "jakarta fund request"},
    {"Name": "DeleteMessage", "Value": "True"},
    {"Name": "StopProcessingRules", "Value": "True"},
    {"Name": "Name", "Value": "Default Rule 1"}
  ]
}
```
## 📝 Ringkasan Jawaban

| No | Question | Answer |
|----|-----------|--------|
| 1  | Phishing sender | yuki.matsuda@kenseicorp.jp |
| 2  | Compromise type | Business Email Compromise |
| 3  | Attacker IPs | 198.51.100.23,203.0.113.45 |
| 4  | Financial institution | CITIBANK N.A. |
| 5  | Mailbox folder | client_archive |
| 6  | Keyword filter | jakarta fund request |
| 7  | Outlook rule name | Default Rule 1 |

## 🎯 Flag
Flag muncul setelah semua pertanyaan berhasil dijawab:
> HIDC2025{P4nc4s1l4_P3m3rs4tu_B4ngs4_Ind0n3s14}