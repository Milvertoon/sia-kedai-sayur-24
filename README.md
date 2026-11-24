# Sistem Informasi Akuntansi Kedai Sayur 24

Repositori bersama untuk membangun sistem informasi akuntansi berbasis web bagi Kedai Sayur 24.

## Keputusan dari pemilik proyek

- Website dengan Python dan database SQLite.
- Anaconda dan Google Colab untuk lingkungan belajar/kerja.
- UML untuk pemodelan sistem.
- Sekitar 30 karyawan.
- Sistem baru menggantikan IPOS setelah cutover.

## Pembagian awal

- Aurellia: data karyawan, absensi, kas dan laporan per shift.
- Syafa: persediaan, POS/penjualan baru, dan laporan periode/bulanan.
- Bersama: UML, aturan bisnis, integrasi antarmodul, serta akuntansi.

## Status fondasi kode

Branch `feat/web-foundation` memuat prototipe awal Django 6.1.3 dan Python 3.12. Django adalah pilihan kerja sementara untuk memulai; Aurel dan Syafa perlu meninjaunya sebelum fitur transaksi dibuat.

Lihat `src/README.md` untuk cara menyiapkan environment dan menjalankan halaman awal.

## Dokumen proyek

- `docs/REQUIREMENTS.md` — kebutuhan awal dan pertanyaan bisnis.
- `docs/ROADMAP.md` — tahapan dan pembagian pekerjaan.
- `docs/ARCHITECTURE.md` — modul dan alur data.
- `docs/DECISION_LOG.md` — keputusan yang sudah pasti dan yang masih terbuka.
- `docs/WORKFLOW.md` — cara kerja GitHub untuk dua pengembang.

## Keamanan

Jangan mengunggah kata sandi, token, database operasional, file ekspor IPOS, atau data pribadi. Gunakan data contoh. Pengaturan untuk produksi belum dibuat.
