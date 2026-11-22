# Catatan Keputusan

Dokumen ini memisahkan fakta yang sudah disampaikan dari pilihan yang masih perlu diputuskan. Perbarui setelah Aurellia dan Syafa sepakat.

## Sudah dikonfirmasi

| Topik | Keputusan |
|---|---|
| Platform | Website |
| Bahasa pemrograman | Python |
| Database | SQLite |
| Lingkungan/tools | Anaconda dan Google Colab |
| Pemodelan sistem | UML |
| Karyawan | Sekitar 30 orang |
| Sistem lama | Sistem baru akan menggantikan IPOS sebagai sistem operasional setelah cutover; IPOS tidak digunakan lagi untuk transaksi operasional |
| Tim | Aurellia dan Syafa membangun satu platform bersama |
| Pembagian awal | Aurellia: data karyawan, absensi, kas/laporan per shift. Syafa: persediaan, POS/penjualan baru, laporan periode/bulanan. Integrasi dan akuntansi lintas modul dikerjakan bersama |

## Perlu disepakati

- Framework dan versi Python. Django adalah usulan, belum keputusan.
- Jumlah dan jam shift, shift lintas tengah malam, pembagian kasir/laci kas, dan aturan tutup kas.
- Tanggal operasional/tutup buku dan siapa yang menyetujui koreksi.
- Detail absensi: toleransi, izin, lembur, dan mekanisme koreksi.
- Produk, satuan dan konversi, susut/barang rusak, stok minimum, dan metode biaya persediaan.
- Metode pembayaran, aturan diskon, pembatalan, dan retur.
- Proses pembelian, pengeluaran operasional, invoice, utang pemasok, dan pembayaran.
- Apakah penggajian termasuk ruang lingkup awal, formula, periode, tunjangan, dan potongan.
- Daftar akun dan laporan akuntansi yang diminta, periode akuntansi, serta saldo awal.
- Cabang/lokasi dan pembagian 30 karyawan per lokasi.
- Riwayat data IPOS yang dibawa/diarsipkan, format ekspor, cutover, dan rekonsiliasi saldo awal.
- Backup/restore, perangkat pengguna, dan cara aplikasi dijalankan saat produksi.

SQLite tetap menjadi database yang dipilih. Sebelum go-live, uji akses serentak, backup, dan pemulihan sesuai perangkat serta pola pemakaian toko.

## Format pencatatan

`Tanggal | Topik | Keputusan | Alasan | Disetujui oleh`
