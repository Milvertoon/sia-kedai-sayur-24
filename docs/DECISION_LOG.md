# Catatan Keputusan

## Keputusan dari proposal final

| Topik | Keputusan |
|---|---|
| Judul penelitian Aurellia | Rancang Bangun Sistem Informasi Akuntansi Berbasis Web Subsistem Absensi Karyawan dan Laporan Keuangan Per Shift pada Kedai Sayur 24 Semarang. |
| Platform | Website. |
| Bahasa/framework | Python dan Django. |
| Database | PostgreSQL. |
| Antarmuka | HTML, CSS, JavaScript, Bootstrap, dan Django Templates. |
| Lingkungan kerja | VS Code sebagai alat pengembangan lokal yang disebut proposal. |
| Pemodelan | UML dan flowchart. |
| Metode pengembangan | Waterfall dengan umpan balik dari evaluasi/pengujian ke kebutuhan/perancangan. |
| Operasional | Tiga cabang Semarang: Sampangan, Fatmawati, Gunungpati; sekitar 30 karyawan; toko beroperasi 24 jam. |
| Jadwal shift | Pagi 08.00–16.00, Tengah 12.00–20.00, Sore 16.00–00.00, Malam 00.00–08.00 WIB. |
| Peran pengguna | Pemilik, manajer, kasir, dan karyawan. |
| Cakupan Aurellia | Absensi dan laporan kas per shift. |
| Cakupan Syafa | POS/penjualan, persediaan, dan laporan berkala/bulanan sesuai pembagian penelitian. |
| Sistem lama | Sistem baru direncanakan menggantikan IPOS setelah migrasi/arsip, rekonsiliasi, pelatihan, dan cutover. |
| Versi fondasi lokal | Repo memulai prototipe dengan Django 6.1.3 dan Python 3.12; versi ini pilihan implementasi fondasi, bukan ketentuan versi eksplisit proposal. |

Keputusan final ini menggantikan catatan kerja sebelumnya yang menetapkan SQLite, Anaconda, dan Google Colab. Sebelum produksi, pilih versi PostgreSQL yang cocok dengan versi Django. Dokumentasi Django 6.1 menyebut PostgreSQL 15+ dan Psycopg 3.1.12+.

## Keputusan proses tim

- Aurellia dan Syafa membangun satu platform dan berbagi standar data.
- Setiap modul memiliki penanggung jawab utama; perubahan kontrak integrasi dan skema lintas modul harus dibahas bersama.
- Aurel mengonsumsi ringkasan pembayaran POS untuk laporan kas, tidak menduplikasi detail transaksi POS.
- Gunakan data contoh selama pengembangan; data nyata karyawan dan transaksi tidak masuk repo.

## Terbuka untuk keputusan pemilik/manajer dan pembimbing

- Status laporan kas untuk shift tengah: tidak ada laporan tersendiri menurut outline, tetapi proposal menyebut laporan per shift.
- Pengelolaan laci kas pada jam shift yang tumpang tindih dan proses serah terima kas.
- Tanggal operasional untuk shift malam yang melewati tengah malam.
- Rumus laporan, klasifikasi uang masuk/keluar, saldo kas seharusnya, selisih, pembayaran tunai/non-tunai, dan setoran.
- Toleransi keterlambatan, izin, pembuktian absensi, radius lokasi, masa simpan selfie/lokasi, serta pihak yang dapat melihatnya.
- Cabang “pusat” untuk pembandingan laporan kas selama tiga hari.
- Hosting, domain, backup, pemulihan, koneksi antar cabang, tanggal cutover IPOS dan data yang perlu dibawa.
- Akun awal, aturan hak akses, dan penanggung jawab persetujuan koreksi.

## Tindak lanjut komentar pembimbing pada outline

- Tegaskan batas penelitian Aurel dan Syafa pada rumusan, tujuan, diagram, antarmuka, metode, serta kontribusi; jangan menyatakan transaksi POS sebagai fitur penelitian Aurel.
- Tampilkan subsistem absensi dan laporan kas per shift sebagai kontribusi Aurel; jelaskan antarmuka data ke modul POS Syafa.
- Jelaskan alur umpan balik pengujian ke kebutuhan/perancangan pada Waterfall.
- Pastikan kasir tetap dipertimbangkan sebagai responden/pengguna untuk skenario tutup kas meskipun POS menjadi cakupan Syafa.
- Rapikan konsistensi tanggal proposal dengan tanggal wawancara/revisi dan lengkapi sitasi/daftar pustaka yang diminta pembimbing. Poin ini tindak lanjut naskah, bukan perubahan fitur aplikasi.

## Format keputusan baru

Tanggal | Topik | Keputusan | Alasan | Disetujui oleh
