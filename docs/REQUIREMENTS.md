# Kebutuhan Sistem dan Batas Penelitian

Dokumen ini mengikuti proposal penelitian final Aurellia. Kebutuhan yang belum diputuskan ditandai sebagai terbuka; jangan jadikan asumsi implementasi.

## Konteks operasional

Kedai Sayur 24 adalah toko ritel 24 jam dengan tiga cabang di Semarang: Sampangan, Fatmawati, dan Gunungpati. Terdapat sekitar 30 karyawan yang dapat ditempatkan di cabang berbeda sesuai kebutuhan. Satu manajer mengawasi operasional.

Jam shift yang tercantum dalam proposal:

| Shift | Jam WIB |
|---|---|
| Pagi | 08.00–16.00 |
| Tengah | 12.00–20.00 |
| Sore | 16.00–00.00 |
| Malam | 00.00–08.00 |

Shift pagi dan tengah, serta tengah dan sore, berjalan bersamaan pada beberapa jam. Laporan harian yang baru dirancang tersedia setelah shift malam selesai, sekitar pukul 08.00 keesokan harinya.

## Batas penelitian Aurellia

Fokus penelitian Aurellia adalah dua subsistem yang saling terhubung:

1. **Absensi karyawan:** identitas karyawan, penempatan cabang dan shift, pencatatan masuk/pulang, status kehadiran, izin, dan riwayat.
2. **Laporan kas per shift:** kas awal, uang masuk, uang keluar, hitung kas fisik, selisih, penutupan, serah terima, dan rekap.

Transaksi detail POS, pengelolaan persediaan, serta laporan keuangan bulanan menjadi modul Syafa. Modul Aurel boleh memakai ringkasan transaksi penjualan/pembayaran dari Syafa sebagai sumber uang masuk, tetapi tidak menduplikasi detail transaksi POS.

Penggajian, perhitungan gaji, dan laporan laba rugi bukan bagian implementasi penelitian Aurellia. Fitur milik Syafa tetap menjadi bagian dari rencana aplikasi bersama sesuai pembagian dan proposal masing-masing.

## Pengguna dan kebutuhan

| Pengguna | Kebutuhan |
|---|---|
| Pemilik | Memantau absensi dan laporan kas shift dari ketiga cabang. |
| Manajer | Mengelola data karyawan dan penempatan cabang/tanggal/shift; memantau absensi; meninjau laporan kas. |
| Kasir | Mencatat uang masuk/keluar yang menjadi tanggung jawabnya, menghitung kas fisik, menutup laporan shift, dan menyerahkan kas. |
| Karyawan | Melakukan absensi sesuai penempatan dan melihat riwayat absensinya sendiri. |

Nama pengguna aplikasi boleh disesuaikan, tetapi pembatasan akses perlu mengikuti peran di atas.

## Kebutuhan fungsional Aurel

| ID | Kebutuhan | Catatan |
|---|---|---|
| A-01 | Login dan hak akses berbasis peran | Pemilik, manajer, kasir, dan karyawan. |
| A-02 | Mengelola data karyawan dan status kerja | Sekitar 30 karyawan. |
| A-03 | Mengelola penempatan karyawan | Cabang, tanggal berlaku, dan shift; simpan riwayat karena karyawan dapat berpindah cabang. |
| A-04 | Mencatat absensi masuk dan pulang | Validasi terhadap jadwal/penempatan yang berlaku. |
| A-05 | Merekam status hadir, terlambat, izin, sakit, dan tidak hadir | Aturan izin dan keterlambatan harus disepakati. |
| A-06 | Merekam bukti selfie dan lokasi saat absensi | Diusulkan proposal; perlu aturan akses, penyimpanan, retensi, dan persetujuan pengguna. |
| A-07 | Mencatat kas awal, uang masuk, dan uang keluar per proses penutupan | Sumber transaksi POS berasal dari modul Syafa sesuai kontrak integrasi. |
| A-08 | Memasukkan hitung kas fisik, menghitung saldo sistem dan selisih | Rumus dan proses pemeriksaan harus sama dengan aturan operasional. |
| A-09 | Menutup dan menyerahkan kas shift | Jejak waktu, pelaksana, dan penerima harus tersimpan. |
| A-10 | Melihat laporan kas per cabang, periode, dan shift yang disepakati | Laporan harian lengkap tersedia pukul 08.00 setelah shift malam selesai. |
| A-11 | Menyediakan riwayat perubahan | Koreksi absensi dan kas harus bisa ditelusuri. |

## Kebutuhan integrasi dengan Syafa

- Satu aplikasi web, satu repositori, satu rancangan data bersama.
- Syafa memiliki transaksi POS, pembayaran, persediaan, dan laporan periode sesuai cakupan penelitiannya.
- Aurel menerima data penjualan/pembayaran yang diperlukan sebagai uang masuk laporan kas tanpa membuat ulang transaksi POS.
- Sebelum kedua modul dikembangkan, sepakati struktur ID cabang, tanggal operasional, shift, kasir, pembayaran, pembatalan/retur, dan waktu transaksi.
- Catat keputusan kontrak integrasi di [DECISION_LOG.md](DECISION_LOG.md) sebelum model data lintas modul dibuat.

## Kebutuhan nonfungsional

- Website berbahasa Indonesia, responsif, menampilkan tanggal/waktu WIB dan rupiah.
- Dukungan pemakaian lintas cabang melalui internet direncanakan untuk penerapan; hosting dan koneksi belum dipilih.
- Kamera dan geolokasi peramban memerlukan izin pengguna dan HTTPS saat dipakai. Data selfie dan lokasi perlu dibatasi aksesnya.
- Perubahan penting memiliki identitas pengguna, waktu, alasan, dan rekam jejak.
- Rahasia konfigurasi berada di file lokal .env yang tidak masuk Git.
- Siapkan pencadangan, pemulihan, serta pelatihan sebelum sistem menggantikan IPOS.

## Hal yang harus diklarifikasi sebelum model data laporan kas dibuat

1. Outline menyebut shift tengah tidak memiliki laporan kas terpisah, sedangkan proposal juga menyebut laporan per shift. Apakah kas shift tengah dicatat sebagai laporan tersendiri, atau masuk ke laporan shift lain?
2. Karena jadwal shift bertumpang tindih, apakah kasir memakai laci kas berbeda, atau beberapa shift memakai kas yang sama? Siapa yang bertanggung jawab saat pergantian?
3. Tanggal mana yang dipakai untuk laporan shift malam yang melewati tengah malam: tanggal mulai shift atau tanggal selesai?
4. Apa rumus saldo awal, uang masuk, uang keluar, saldo seharusnya, kas fisik, dan selisih? Bagaimana setoran bank dan pembayaran non-tunai diperlakukan?
5. Apakah kasir yang menutup shift harus sama dengan kasir yang ditugaskan? Siapa yang menyetujui koreksi atau selisih?
6. Bagaimana aturan toleransi keterlambatan, izin, sakit, lupa absen, selfie/lokasi gagal, dan koreksi absensi?
7. Cabang mana yang dimaksud sebagai cabang pusat pada rencana pengujian rekonsiliasi kas?
8. Apa data historis IPOS yang perlu diarsipkan atau dimigrasikan sebelum cutover?

## Rencana evaluasi penelitian

Proposal menyebut pengujian Black Box menggunakan equivalence partitioning dan boundary value analysis, pengukuran kemudahan penggunaan memakai 10 pernyataan SUS dengan skala Likert 5 poin, serta pembandingan laporan kas sistem dengan perhitungan manual selama tiga hari. Rincian skenario, responden, cabang, dan rumus pembanding perlu dicantumkan di naskah dan disepakati dengan pembimbing.
