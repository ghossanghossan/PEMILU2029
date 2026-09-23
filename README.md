# Database Simulasi Pasangan Calon

Dasbor sederhana untuk data simulasi/fiktif, dibangun untuk menguji alur:
**Google Sheets → Apps Script (API) → GitHub Pages (tampilan)**.

> Data di sini bersifat simulasi/fiktif untuk pengujian database — bukan hasil survei, quick count, exit poll, atau prediksi Pemilu.

## Isi repo

- `index.html` — halaman dasbor (bisa langsung dibuka di browser atau dihosting via GitHub Pages).
- `Code.gs` — backend Google Apps Script yang menyajikan data sheet sebagai JSON API.

## Cara pasang

### 1. Google Sheets + Apps Script
1. Buka Google Sheet berisi sheet `Database Simulasi` dan `Catatan` (sesuai file Excel aslinya).
2. Buka **Ekstensi → Apps Script**, tempel isi `Code.gs` ke `Code.gs` di editor.
3. **Deploy → Kelola Penerapan → Penerapan Baru**:
   - Jenis: **Aplikasi Web**
   - Execute as: **Saya (Me)**
   - Siapa yang punya akses: **Siapa saja (Anyone)**
4. Salin URL yang berakhiran `/exec`.

### 2. GitHub Pages
1. Buat repo baru, unggah `index.html`.
2. Buka `index.html`, cari baris:
   ```js
   const API_URL = "";
   ```
   Isi dengan URL Apps Script dari langkah di atas.
3. Aktifkan **Settings → Pages → Deploy from branch → main / root**.
4. Situs akan tersedia di `https://<username>.github.io/<nama-repo>/`.

Jika `API_URL` dikosongkan atau gagal diakses, dasbor otomatis memakai data cadangan yang sudah tersimpan di dalam `index.html`, jadi situs tetap bisa dibuka tanpa Apps Script.

## Menambah data lewat API (opsional)

`Code.gs` sudah menyediakan `doPost` untuk menambah jumlah responden:

```bash
curl -X POST "<API_URL>" -d '{"wilayah":"Jawa","kolom":"Purbaya–Sherly","jumlah":5}'
```
