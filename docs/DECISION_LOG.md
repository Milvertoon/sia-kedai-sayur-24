# Catatan Keputusan

Dokumen ini memisahkan fakta yang sudah disampaikan dari pilihan yang masih perlu diputuskan. Perbarui status dan tanggal ketika ada kesepakatan.

## Sudah dikonfirmasi

| Topik | Keputusan |
|---|---|
| Bentuk sistem | Aplikasi web baru untuk sistem informasi akuntansi toko sayur |
| Karyawan | Sekitar 30 karyawan |
| Sistem lama | Sistem baru direncanakan menggantikan IPOS sepenuhnya setelah cutover; IPOS tidak menjadi sistem operasional setelah itu |
| Tim | Aurellia dan Syafa membangun satu platform bersama |
| Pemodelan | UML |
| Pembagian awal | Aurellia: absensi dan kas/laporan per shift. Syafa: persediaan, POS/penjualan baru, laporan periode/bulanan. Integrasi dan validasi dilakukan bersama |

## Perlu disepakati sebelum implementasi terkait

- Framework Python dan versi yang digunakan.
- Database final: SQLite atau PostgreSQL. Pilihan harus mempertimbangkan akses bersamaan, pencadangan, dan lingkungan produksi.
- Aturan shift: jumlah/nama shift, pergantian hari, shift lintas tengah malam, shift tumpang tindih, dan penanggung jawab kas.
- Tanggal operasional dan waktu tutup buku harian.
- Proses tutup kas: uang awal, uang aktual, selisih, persetujuan, dan koreksi.
- Sumber pencatatan biaya/pengeluaran dan siapa yang boleh mencatat/menyetujui.
- Cabang/lokasi dan pembagian 30 karyawan per lokasi.
- Peran pengguna dan hak akses (misalnya admin, manajer, kasir, petugas persediaan, keuangan).
- Data historis IPOS yang perlu dibawa, format ekspor, saldo awal, masa arsip, rencana cutover, dan cara rekonsiliasi.
- Ketentuan backup, hosting, dan siapa yang mengelola deployment.

## Cara mencatat keputusan

Tambahkan baris dengan format: `Tanggal | Topik | Keputusan | Alasan | Disetujui oleh`. Jangan menganggap isi dokumen referensi sebagai keputusan final sebelum dikonfirmasi oleh pemilik proses.
