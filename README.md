# Sistem Informasi Akuntansi Kedai Sayur 24

Repositori bersama Aurellia dan Syafa untuk merancang dan membangun sistem informasi akuntansi berbasis web. Sistem baru ditujukan untuk menggantikan IPOS setelah proses cutover dan kesiapan data disepakati.

## Keputusan yang sudah diberikan

- Platform: website.
- Bahasa: Python.
- Database: SQLite.
- Tools yang direncanakan: Anaconda dan Google Colab.
- Pemodelan: UML.
- Jumlah karyawan: 30 orang.
- Sistem baru akan menggantikan IPOS sebagai sistem operasional setelah go-live.

Framework Python, aturan shift, metode persediaan, dan rincian migrasi masih perlu dikunci. Lihat [`docs/DECISION_LOG.md`](docs/DECISION_LOG.md).

## Pembagian awal tim

- **Aurellia:** data karyawan, absensi, kas dan laporan per shift.
- **Syafa:** persediaan, penjualan/POS baru, dan laporan periode/bulanan.
- **Bersama:** kebutuhan lintas modul, UML, integrasi, akuntansi, review, dan persiapan cutover.

## Status saat ini

Repo dan alur GitHub sudah disiapkan. Tahap yang sedang berjalan adalah menyepakati kebutuhan serta aturan bisnis sebelum membuat skema database dan fitur aplikasi.

## Dokumen kerja

- [`docs/REQUIREMENTS.md`](docs/REQUIREMENTS.md) — kebutuhan awal dan hal yang perlu dikonfirmasi.
- [`docs/ROADMAP.md`](docs/ROADMAP.md) — tahapan pembangunan dan pembagian kerja.
- [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) — modul dan alur data konseptual.
- [`docs/DECISION_LOG.md`](docs/DECISION_LOG.md) — keputusan terkonfirmasi dan terbuka.
- [`docs/WORKFLOW.md`](docs/WORKFLOW.md) — branch, pull request, dan integrasi dua pengembang.

## Keamanan data

Jangan commit kata sandi, token, database produksi, ekspor IPOS, atau data pribadi karyawan/pelanggan. Gunakan data sintetis. Rahasia lokal disimpan dalam `.env` yang tidak di-commit.
