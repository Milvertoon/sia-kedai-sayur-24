# Sistem Informasi Akuntansi Kedai Sayur 24

Repositori untuk membangun satu aplikasi web bagi Kedai Sayur 24 Semarang. Rancangan terbaru mengikuti proposal penelitian Aurellia: skripsinya berfokus pada subsistem absensi karyawan dan laporan kas per shift. Sistem keseluruhan juga akan terhubung dengan modul yang dikerjakan Syafa.

## Acuan rancangan terbaru

- Platform: website.
- Bahasa: Python dengan Django.
- Database: PostgreSQL.
- Antarmuka: HTML, CSS, JavaScript, Bootstrap, dan Django Templates.
- Perangkat kerja utama: VS Code.
- Pemodelan: UML dan flowchart.
- Pengguna: pemilik, manajer, kasir, dan karyawan.
- Operasional: tiga cabang di Semarang, sekitar 30 karyawan, toko buka 24 jam, empat shift.
- Sistem baru direncanakan menggantikan IPOS setelah data, proses, pelatihan, dan cutover siap.

Proposal final menggantikan pilihan kerja lama yang menyebut SQLite, Anaconda, dan Google Colab. Prototipe repo sudah menggunakan Django; konfigurasinya sedang diselaraskan ke PostgreSQL.

## Pembagian kerja

- **Aurellia (Aurel):** data dan penempatan karyawan, absensi, serta laporan kas per shift. Modul laporan Aurel menerima data penjualan/pembayaran dari modul Syafa sesuai kontrak integrasi yang disepakati.
- **Syafa:** persediaan, transaksi POS/penjualan, dan laporan keuangan per periode/bulanan sesuai pembagian penelitian.
- **Bersama:** login dan hak akses, data cabang/shift, UML, aturan bisnis, kontrak integrasi, akuntansi bersama, peninjauan perubahan, dan integrasi sistem.

Pembagian ini menjelaskan kepemilikan kerja; produk tetap satu aplikasi dan satu repositori.

## Status repo

Branch lokal saat ini adalah feat/web-foundation. Isinya fondasi Django dan halaman awal, belum berisi fitur operasional atau transaksi. Perubahan berdasarkan proposal final disiapkan di branch lokal ini agar dapat ditinjau sebelum dikirim ke GitHub.

## Dokumen proyek

- [docs/REQUIREMENTS.md](docs/REQUIREMENTS.md) — kebutuhan dan batas penelitian.
- [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) — modul serta aliran data.
- [docs/DECISION_LOG.md](docs/DECISION_LOG.md) — keputusan final dan hal yang masih harus dipastikan.
- [docs/ROADMAP.md](docs/ROADMAP.md) — urutan pengerjaan dan pembagian dua orang.
- [docs/WORKFLOW.md](docs/WORKFLOW.md) — cara kerja Git dan pull request.
- [src/README.md](src/README.md) — cara menyiapkan dan menjalankan fondasi lokal.

## Data dan keamanan

Gunakan data contoh sintetis. Jangan unggah kata sandi, token, database operasional, ekspor IPOS, foto selfie, lokasi, atau data pribadi karyawan. Jangan gunakan server pengembangan Django sebagai aplikasi toko.
