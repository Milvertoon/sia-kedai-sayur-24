# Gambaran Arsitektur (Draf)

## Prinsip

- Satu aplikasi web untuk operasional dan akuntansi.
- Satu repositori GitHub dan satu basis kode yang dikerjakan melalui branch.
- Pisahkan modul berdasarkan tanggung jawab bisnis, tetapi sepakati model data bersama sebelum integrasi.
- Catat perubahan penting dan pembuatnya agar alur transaksi dapat diaudit.

## Modul yang direncanakan

| Modul | Penanggung jawab awal | Ruang lingkup |
|---|---|---|
| `core` | Bersama | Konfigurasi, identitas toko/cabang, audit dasar |
| `accounts` | Bersama | Login, pengguna, peran, dan hak akses |
| `employees` | Aurellia | Data karyawan dan penempatan kerja |
| `attendance` | Aurellia | Absensi, jadwal, keterlambatan, rekap |
| `shift_cash` | Aurellia | Sesi kas/shift, kas awal, kas akhir, selisih, laporan shift |
| `inventory` | Syafa | Produk, satuan, kategori, pemasok, penerimaan, penyesuaian dan kartu stok |
| `sales` | Syafa | POS/penjualan baru, detail penjualan, pembayaran, pembatalan/retur yang disetujui; menggantikan proses penjualan IPOS |
| `period_reports` | Syafa + Aurellia | Laporan bulanan/periode yang mengambil data dari modul terkait |

Nama modul di atas adalah pengelompokan konseptual, bukan komitmen struktur kode final.

## Alur data tingkat tinggi

Penjualan yang diselesaikan mengurangi stok dan menghasilkan ringkasan penerimaan kas. Sesi shift mengelompokkan kas berdasarkan aturan operasional yang disepakati. Data penjualan, pembelian/penerimaan, biaya, penggajian, dan penyesuaian stok menjadi masukan laporan keuangan sesuai kebijakan akuntansi toko.

## Batas rancangan

Framework, database, struktur aplikasi Django, skema akun, metode valuasi persediaan, dan mekanisme migrasi IPOS belum diputuskan. Hindari membuat tabel atau endpoint yang mengasumsikan jawaban untuk keputusan tersebut. Lihat [`DECISION_LOG.md`](DECISION_LOG.md).
