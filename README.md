# FormDX v1.0 — Sistem Manajemen Formulasi R&D

> **Restart Bersih**: Aplikasi ini adalah versi baru yang telah di-debug dan dibersihkan dari bug koneksi database yang sebelumnya terjadi. Semua fitur utama tetap dipertahankan, dengan manajemen koneksi yang lebih stabil.

## Fitur Utama

- **Autocomplete Bahan Baku**: Ketik minimal 2 huruf → hasil muncul otomatis, klik untuk pilih.
- **Stock Card Otomatis**: Saat membuat Trial dengan centang "Update stok otomatis", pergerakan stok (IN/OUT) tercatat otomatis dengan referensi No. Formula & Nama Produk. Bisa export CSV/PDF.
- **Fase Input Teks Bebas**: Kolom fase per bahan bisa diketik bebas (bukan dropdown).
- **Manajemen Bahan Baku**: CRUD lengkap + filter "Tampilkan hanya stok menipis".
- **Riwayat Trial**: Dikelompokkan per Nama Produk, dengan audit history (CREATE/UPDATE/DELETE).
- **Export**: Kartu Stok ke CSV/PDF, Trial ke PDF profesional.
- **Inbound Stock**: Tambah stok manual dengan No. LPB.

## Perbaikan di v1.0 (Clean Restart)

- Database Locked Error diperbaiki:
  - `PRAGMA journal_mode = WAL`
  - `PRAGMA busy_timeout = 30000`
  - `flask.g` + `teardown_appcontext` untuk koneksi per-request yang robust + auto-recovery.
- Filter stok menipis berfungsi benar.
- Branding bersih FormDX v1.0 (tidak ada sisa FormuTrack / FormuDex).
- Audit log (trial_history) sekarang selalu tersimpan dengan benar.
- Export Stock Card CSV menggunakan urutan kronologis yang benar.
- Form Create Trial dilengkapi field Objective & Prosedur (konsisten dengan Edit & DB).

## Cara Menjalankan (macOS / Linux / Windows)

```bash
cd formudex_v1

python3 -m venv venv
source venv/bin/activate          # Windows: venv\Scripts\activate

pip install -r requirements.txt
python3 app.py
```

Buka browser: **http://127.0.0.1:5000**

**Login default:**
- Username: `formulator`
- Password: `rd2026`
- (atau `admin` / `admin123`)

> **Catatan:**
> - Python 3.10+ direkomendasikan.
> - macOS: `brew install python` jika belum ada.
> - Setelah jalankan, tekan `Ctrl + C` di terminal untuk stop server.
> - Database: `formdx.db` (otomatis dibuat + sample data tablet excipients).

