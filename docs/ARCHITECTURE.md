# Gambaran Arsitektur (Draf)

## Prinsip

- Satu aplikasi web untuk operasional dan akuntansi.
- Satu repositori GitHub, satu basis kode, dan satu SQLite database pada konfigurasi awal yang telah dipilih.
- Pisahkan tanggung jawab bisnis ke modul, tetapi sepakati model dan kontrak integrasi bersama sebelum fitur lintas modul dibuat.
- Transaksi penting dan koreksi dapat ditelusuri ke akun pengguna serta sumber transaksi.

## Modul konseptual

| Modul | Penanggung jawab awal | Ruang lingkup |
|---|---|---|
| `core` | Bersama | Konfigurasi, data toko/lokasi, periode operasional, audit |
| `accounts` | Bersama | Login, pengguna, peran, dan hak akses |
| `employees` | Aurellia | Data karyawan dan penempatan |
| `attendance` | Aurellia | Jadwal, absensi, keterlambatan, izin, koreksi, rekap |
| `shift_cash` | Aurellia | Sesi shift, kas awal/akhir, selisih, penutupan, laporan shift |
| `inventory` | Syafa | Produk, kategori, satuan, pemasok, penerimaan, penyesuaian, kartu stok |
| `sales` | Syafa | POS baru, detail penjualan, pembayaran, void/retur terkontrol; menggantikan transaksi IPOS |
| `purchasing` | Syafa + Keuangan | Pesanan/penerimaan pembelian, invoice pemasok, utang dan pembayaran |
| `expenses` | Keuangan | Biaya operasional dan bukti pendukung |
| `payroll` | Aurellia + Keuangan | Perhitungan gaji dari aturan yang disepakati dan laporan gaji |
| `accounting` | Bersama | Daftar akun, jurnal, buku besar, neraca saldo, tutup periode |
| `reports` | Syafa + Aurellia | Laporan penjualan, stok, kas/shift, absensi, penggajian, dan laporan keuangan |

## Alur data tingkat tinggi

Penjualan yang dibayar mengurangi stok dan mencatat penerimaan berdasarkan metode pembayaran. Pembelian yang diterima menambah stok dan dapat mencatat utang pemasok. Pengeluaran, penggajian, retur, setoran kas, dan koreksi stok memiliki transaksi sumber dan aturan persetujuan. Modul akuntansi memetakan transaksi tersebut ke jurnal sehingga laporan bisa ditelusuri kembali.

## Fondasi kode saat ini

Branch `feat/web-foundation` berisi prototipe Django 6.1.3 dan Python 3.12 dengan satu halaman awal, konfigurasi SQLite, serta environment Anaconda. Belum ada model data atau alur transaksi. Framework ini adalah pilihan awal; tinjau bersama sebelum modul bisnis dibuat.

SQLite adalah pilihan database yang sudah diberikan. Setiap pengembang sebaiknya memiliki database pengembangan sendiri; jangan sinkronkan file SQLite yang sedang aktif lewat Git/OneDrive. Siapkan backup berkala dan validasi transaksi saat penggunaan serentak sebelum go-live. Anaconda dapat mengelola environment Python lokal; Google Colab digunakan untuk eksperimen yang sesuai, bukan sebagai tempat penyimpanan database operasional.
