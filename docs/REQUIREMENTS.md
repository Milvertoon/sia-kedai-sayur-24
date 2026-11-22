# Kebutuhan Awal Sistem

Dokumen ini merangkum kebutuhan berdasarkan informasi Aurellia. Isinya adalah baseline untuk ditinjau, bukan persetujuan rinci terhadap aturan bisnis yang masih ditandai **perlu konfirmasi**.

## Tujuan dan ruang lingkup

Membangun satu aplikasi web baru yang menghubungkan operasional toko sayur dengan pencatatan akuntansi. Sistem mencakup sekitar 30 karyawan dan menggantikan IPOS setelah data awal, proses, dan cutover siap.

## Pengguna sistem

| Pengguna | Kebutuhan awal |
|---|---|
| Admin/pemilik | Mengatur pengguna, peran, data toko, dan konfigurasi |
| Manajer | Memantau operasional, menyetujui koreksi tertentu, melihat laporan |
| Kasir | Mencatat transaksi POS dan melakukan penutupan kas sesuai shift |
| Petugas persediaan | Mengelola produk, penerimaan, perpindahan, dan koreksi stok |
| Keuangan | Mencatat/memeriksa jurnal, utang, biaya, penggajian, dan laporan |
| Karyawan | Data kepegawaian dan absensi; akses mandiri belum diputuskan |

Nama peran dan batas hak akses final perlu disepakati.

## Kebutuhan fungsional awal

| ID | Fitur | Prioritas awal | Catatan |
|---|---|---|---|
| F-01 | Login, logout, pengelolaan pengguna dan hak akses | Wajib | Setiap tindakan penting dikaitkan dengan akun pengguna |
| F-02 | Data karyawan dan status kerja | Wajib | Menangani sekitar 30 orang |
| F-03 | Jadwal dan absensi karyawan | Wajib | Aturan shift, keterlambatan, izin, dan koreksi perlu dikonfirmasi |
| F-04 | Data produk, kategori, satuan, dan pemasok | Wajib | Satuan jual dan satuan beli dapat berbeda; konversi perlu ditentukan |
| F-05 | Penerimaan pembelian dan pergerakan persediaan | Wajib | Setiap perubahan stok harus memiliki alasan dan jejak pengguna |
| F-06 | POS/penjualan baru | Wajib | Pencatatan penjualan menggantikan IPOS pada saat go-live |
| F-07 | Pembayaran, pembatalan, retur, dan diskon | Wajib | Metode pembayaran dan aturan persetujuan perlu ditentukan |
| F-08 | Sesi kas dan laporan per shift | Wajib | Kas awal, kas akhir, setoran, selisih, dan penanggung jawab perlu dikonfirmasi |
| F-09 | Biaya operasional dan utang pemasok | Penting | Termasuk pencatatan invoice, pembayaran, dan saldo utang |
| F-10 | Penggajian dan laporan penggajian | Penting | Rumus upah, tunjangan, potongan, dan periode perlu ditentukan |
| F-11 | Jurnal, buku besar, dan neraca saldo | Wajib untuk akuntansi | Transaksi sumber menghasilkan jurnal yang dapat ditelusuri |
| F-12 | Laporan laba rugi, neraca, dan laporan arus kas | Wajib untuk akuntansi | Periode, saldo awal, dan kebijakan akuntansi perlu disepakati |
| F-13 | Laporan penjualan, persediaan, absensi, dan penggajian per periode | Wajib | Filter tanggal dan hak akses mengikuti peran |
| F-14 | Pengaturan toko, akun, shift, dan periode akuntansi | Wajib | Isi pengaturan final mengikuti hasil analisis |
| F-15 | Audit perubahan dan ekspor/cetak laporan | Penting | Perlu menentukan laporan mana yang perlu diekspor atau dicetak |

## Aturan integritas yang direkomendasikan

- Penjualan yang berhasil disimpan harus tercatat satu kali, mengurangi stok, dan memperbarui ringkasan pembayaran secara konsisten.
- Pembatalan atau retur menggunakan transaksi pembalik/jejak koreksi; transaksi keuangan yang sudah diposting tidak dihapus diam-diam.
- Pergerakan stok, perubahan kas, dan jurnal menyimpan waktu serta akun pengguna yang melakukan perubahan.
- Total debit dan kredit jurnal harus seimbang.
- Laporan per shift dan laporan bulanan harus dapat ditelusuri ke transaksi sumber.
- Penutupan periode dan siapa yang boleh membukanya kembali perlu ditentukan.

## Kebutuhan nonfungsional awal

- Antarmuka web responsif untuk komputer kasir dan perangkat yang tersedia di toko.
- Bahasa Indonesia, tanggal/jam yang jelas, dan nilai rupiah.
- Hak akses berbasis peran; kata sandi disimpan secara aman; sesi yang tidak aktif ditangani dengan benar.
- Pencadangan database rutin dan prosedur pemulihan sebelum go-live.
- Dapat digunakan tim sekitar 30 karyawan; beban pengguna serentak dan perangkat yang dipakai perlu diukur.
- SQLite adalah database yang sudah dipilih. Sebelum produksi, validasi akses serentak, lokasi file database, pencadangan, dan pemulihan agar transaksi kasir tidak terkunci atau hilang.
- Lingkungan lokal dikelola konsisten oleh tim. Google Colab dapat dipakai untuk eksplorasi/notebook, tetapi sumber kode utama dan database bersama tetap dikelola melalui repo serta lingkungan aplikasi yang disepakati.

## Batas awal

Sistem produksi/manufaktur dan BOM belum dimasukkan karena kebutuhan yang diketahui adalah toko sayur ritel. Jika toko mengolah atau mengemas produk dengan resep/komposisi, kebutuhan itu ditambahkan setelah dikonfirmasi.

## Pertanyaan bisnis yang harus dijawab sebelum desain data final

1. Berapa jumlah shift sehari, jam mulai/selesai, apakah ada shift lintas tengah malam, dan apakah setiap shift memiliki kasir/laci kas sendiri?
2. Bagaimana aturan absensi: sumber jam masuk, toleransi keterlambatan, izin, lupa absen, lembur, dan siapa yang menyetujui koreksi?
3. Produk dijual berdasarkan satuan apa (kg, ikat, buah, pak, dll.)? Bagaimana menangani konversi, susut, barang rusak/busuk, dan stok minimum?
4. Metode biaya persediaan yang digunakan apa, dan apakah harga beli harus dicatat per penerimaan?
5. Metode pembayaran yang diterima apa? Siapa yang boleh memberi diskon, membatalkan transaksi, menyetujui retur, dan menutup kas?
6. Pengeluaran dan utang pemasok dicatat oleh siapa? Apakah pembelian selalu memakai invoice dan pembayaran dapat dicicil?
7. Penggajian dihitung bulanan, harian, per shift, atau kombinasi? Apa komponen tunjangan/potongannya?
8. Laporan akuntansi apa saja yang wajib untuk skripsi dan operasional? Apakah ada saldo awal akun/aset/utang yang perlu dimasukkan?
9. Data apa dari IPOS yang perlu diimpor/diarsipkan, kapan cutover dilakukan, dan bagaimana saldo awal stok direkonsiliasi?
10. Apakah hanya satu toko/lokasi? Siapa pemilik proses yang menyetujui data dan transaksi?
