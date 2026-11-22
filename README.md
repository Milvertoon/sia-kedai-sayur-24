# Sistem Informasi Akuntansi Kedai Sayur 24

Repositori kerja bersama untuk merancang dan membangun sistem informasi akuntansi berbasis web bagi Kedai Sayur 24. Sistem baru direncanakan menggantikan IPOS setelah proses cutover disepakati dan data yang dibutuhkan siap.

## Status

Repositori ini adalah kerangka awal untuk kolaborasi dan dokumentasi keputusan. Fitur aplikasi belum mulai diimplementasikan karena beberapa aturan operasional dan pilihan teknologi masih perlu dikonfirmasi.

## Pembagian awal

- **Aurellia:** absensi karyawan dan kas/laporan per shift.
- **Syafa:** persediaan, penjualan/POS baru (menggantikan alur IPOS), serta laporan periode/bulanan.
- **Bersama:** aturan bisnis, integrasi, rancangan UML, review, dan penerimaan sistem.

Jumlah karyawan yang direncanakan: **30 orang**.

## Usulan teknis yang menunggu persetujuan

- Website dengan Python; Django diusulkan sebagai kerangka kerja.
- Database bersama. PostgreSQL diusulkan untuk penggunaan multi-pengguna; SQLite pernah disebut sebagai pilihan awal, sehingga keputusan final perlu disepakati sebelum membangun skema.
- UML untuk pemodelan.
- GitHub untuk repositori dan pull request; setiap orang mengembangkan di branch terpisah.

## Mulai bekerja

1. Baca [`docs/DECISION_LOG.md`](docs/DECISION_LOG.md) dan tambahkan keputusan yang sudah disepakati.
2. Tinjau [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) serta [`docs/WORKFLOW.md`](docs/WORKFLOW.md).
3. Setujui pilihan stack dan aturan penting (shift, tanggal operasional, kas, migrasi/cutover IPOS).
4. Setelah itu, buat rancangan UML dan skema data yang disepakati sebelum implementasi modul.

## Keamanan dan data

Jangan commit kata sandi, token, file database produksi, salinan data karyawan/pelanggan, atau data transaksi nyata. Gunakan data contoh tanpa identitas pribadi. Simpan rahasia lokal di `.env` yang tidak di-commit.
