# 🧠 Personal Automation Workflows with n8n

Ini adalah repository berisi **workflow otomatisasi pribadi** yang saya buat menggunakan [n8n](https://n8n.io), sebuah platform automasi open-source yang powerful dan fleksibel.

Tujuannya adalah untuk menyelesaikan berbagai **pekerjaan repetitif harian**, meningkatkan efisiensi, dan mengurangi pekerjaan manual, khususnya dalam hal pencatatan keuangan, pengelolaan file, dan notifikasi.

---

## 🔧 Teknologi & Tools
- [n8n](https://n8n.io): Workflow automation tool (self-hosted)
- [Telegram Bot](https://core.telegram.org/bots): Untuk input dan interaksi user
- Google Drive API: Menyimpan file secara otomatis
- Google Sheets API: Mencatat data terstruktur ke spreadsheet
- OCR API / Tesseract: Mengekstrak teks dari gambar
- Excel Parser (XLSX): Membaca isi file Excel yang dikirim lewat Telegram

---

## 📌 Workflow yang Tersedia

### 1. **Catat Keuangan dari Screenshot**
- Input: Gambar struk atau transaksi via Telegram
- Proses:
  - Simpan file ke Google Drive dalam folder `/Keuangan/{Bulan Tahun}`
  - Ekstrak teks dari gambar menggunakan OCR
  - Parsing dan normalisasi data
  - Simpan ke Google Sheets sesuai kolom
- Output: Baris baru di spreadsheet dengan informasi transaksi

### 2. **Upload File Excel dan Catat Otomatis**
- Input: File `.xlsx` dikirim lewat Telegram
- Proses:
  - Baca isi file Excel
  - Parsing tiap baris (sesuai struktur tertentu)
  - Simpan ke Google Sheets
- Output: Data tercatat secara otomatis di spreadsheet yang sesuai

### 3. **Cek Pengeluaran via Chat**
- Input: Perintah dari Telegram (misal: `/cekbulan September`)
- Output: Bot akan membalas dengan total pengeluaran bulan tersebut

### (Opsional / Coming Soon)
- Reminder otomatis
- Laporan mingguan via chat
- Sinkronisasi dengan aplikasi lain (Notion, Calendar, dll.)

---

## 📁 Struktur Folder Google Drive
```
/Keuangan
  /September 2025
    - IMG_2025-09-01.jpg
    - BuktiTransfer-02.jpg
```

---

## 📄 Format Kolom di Google Sheets

| Tanggal     | Kategori | Deskripsi         | Nominal  | Sumber |
|-------------|----------|-------------------|----------|--------|
| 2025-09-01  | Makan    | Ayam geprek gojek | 22,000   | OVO    |

---

## 🚀 Cara Menjalankan
> Untuk pengguna pribadi yang sudah menjalankan n8n (self-hosted)

1. Clone repo ini
2. Import file workflow `.json` ke dalam n8n
3. Tambahkan kredensial untuk:
   - Telegram Bot
   - Google Drive & Sheets API
4. Sesuaikan spreadsheet ID, folder ID, dan parameter lainnya
5. Jalankan workflow secara manual atau aktifkan trigger (otomatis)

---

## 🛠 Pengaturan Tambahan
- Gunakan [Webhook URL] untuk testing lokal
- Pastikan format file dari Telegram tidak diubah (harus `image/jpeg` atau `application/vnd.openxmlformats-officedocument.spreadsheetml.sheet`)
- Gunakan [Cron Node] untuk proses berkala (misal laporan mingguan)

---

## 🧩 Tips Penggunaan
- Bisa digabung dengan tools seperti Zapier, Make.com, atau Notion
- Tambahkan notifikasi jika parsing gagal
- Gunakan label/tag di Telegram untuk memfilter jenis transaksi

---

## 📚 Lisensi
MIT License. Bebas digunakan dan dimodifikasi untuk keperluan pribadi.

---

## 🙌 Kontribusi / Feedback
Jika kamu juga punya workflow menarik atau ide lain, feel free to fork atau buka issue 🙌
