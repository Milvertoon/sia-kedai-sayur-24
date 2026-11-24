# Catatan Keputusan

Dokumen ini memisahkan keputusan yang sudah diberikan dari pilihan awal prototipe dan aturan bisnis yang masih perlu disepakati.

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

## Pilihan awal untuk prototipe

| Topik | Pilihan kerja | Status |
|---|---|---|
| Framework | Django 6.1.3 | Dipakai untuk fondasi awal; tinjau bersama sebelum membuat fitur transaksi |
| Versi Python | Python 3.12 | Versi dasar di environment Anaconda; dapat diubah jika komputer tim mensyaratkan versi lain |
| Zona waktu | Asia/Jakarta | Default sementara; konfirmasi lokasi operasional toko |

## Perlu disepakati

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
