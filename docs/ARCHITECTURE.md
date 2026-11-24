# Gambaran Arsitektur

## Bentuk aplikasi

Aplikasi berupa satu website Django dengan PostgreSQL. Satu repositori menaungi modul bersama dan modul yang menjadi tanggung jawab masing-masing mahasiswa. Database lokal setiap orang untuk pengembangan; data tidak disalin lewat Git.

## Modul dan pemilik kerja

| Modul | Pemilik utama | Tanggung jawab |
|---|---|---|
| Fondasi aplikasi | Bersama | Konfigurasi, layout, login/logout, keamanan dasar, navigasi. |
| Pengguna dan hak akses | Bersama | Peran pemilik, manajer, kasir, karyawan; aturan akses. |
| Cabang, shift, penempatan | Bersama | Data tiga cabang, jadwal empat shift, tanggal operasional, penugasan karyawan/kasir. |
| Karyawan | Aurellia | Profil, status kerja, dan riwayat penempatan yang diperlukan absensi. |
| Absensi | Aurellia | Jam masuk/pulang, status, izin, bukti selfie/lokasi, riwayat dan rekap. |
| Laporan kas shift | Aurellia | Uang awal/masuk/keluar, hitung kas, selisih, penutupan, serah terima, laporan harian. |
| POS dan penjualan | Syafa | Transaksi penjualan, detail barang, pembayaran, pembatalan/retur terkontrol. |
| Persediaan | Syafa | Produk, satuan, penerimaan dan pergerakan stok. |
| Laporan periode | Syafa | Laporan penjualan dan keuangan berkala sesuai penelitian Syafa. |
| Pelaporan gabungan | Bersama | Hak akses dan tampilan lintas modul yang telah disepakati. |

Nama aplikasi Django dapat ditetapkan setelah rancangan UML/domain disepakati. Jangan membuat model bisnis lintas modul hanya dari tabel di atas.

## Aliran data utama

1. Manajer menetapkan karyawan, cabang, tanggal berlaku, dan shift.
2. Karyawan melakukan absensi masuk/pulang; sistem memeriksa penempatannya dan menyimpan waktu/status serta bukti yang diizinkan.
3. Modul POS Syafa menyimpan transaksi dan pembayaran.
4. Laporan kas Aurel membaca ringkasan pembayaran yang relevan sebagai uang masuk. Detail baris transaksi dan pengurangan stok tetap dimiliki modul Syafa.
5. Kasir mencatat uang keluar dan kas fisik, kemudian menutup serta menyerahkan kas.
6. Pemilik/manajer meninjau laporan per cabang dan periode. Rekap harian lengkap tersedia setelah shift malam selesai pada pukul 08.00 WIB.

## Kontrak integrasi sebelum coding lintas modul

Sepakati satu sumber data dan pemilik untuk cabang, shift, tanggal operasional, penugasan kasir, transaksi, pembayaran, retur/pembatalan, dan status penutupan. Tentukan apakah laporan kas mengambil data langsung dari transaksi pembayaran atau melalui ringkasan yang disiapkan Syafa. Perubahan kontrak dikomunikasikan lewat issue/pull request dan dicatat di decision log.

## Risiko rancangan yang masih terbuka

Shift pagi/tengah dan tengah/sore bertumpang tindih. Outline menyatakan shift tengah tidak memiliki laporan kas tersendiri, sementara proposal memerlukan laporan per shift dan laporan harian. Sebelum membuat tabel/model sesi kas, putuskan apakah tiap shift memakai laci sendiri, memakai laci yang sama, atau ada model serah terima lain. Tentukan juga tanggal akuntansi untuk shift malam yang melintasi tengah malam.

## Fondasi kode saat ini

Branch feat/web-foundation berisi halaman awal Django. Konfigurasi database sedang dipindahkan ke PostgreSQL mengikuti proposal. Belum tersedia model atau alur absensi, POS, persediaan, maupun kas. Django 6.1 memerlukan PostgreSQL 15 atau lebih baru dan Psycopg 3.1.12 atau lebih baru; cek versi server yang dipilih sebelum instalasi.
