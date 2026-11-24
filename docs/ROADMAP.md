# Roadmap Pembangunan

Urutan ini mengikuti proposal penelitian terbaru dan pembagian dua orang untuk satu aplikasi. Waterfall menjadi alur utama, dengan putaran umpan balik ketika uji coba menemukan masalah pada kebutuhan atau rancangan.

## Tahap 0 — Acuan dan batas penelitian

**Aurellia:** pastikan cakupan naskahnya absensi dan laporan kas per shift.
**Syafa:** pastikan pemilik modul POS, persediaan, dan laporan periode.
**Bersama:** tandai keputusan yang perlu persetujuan pemilik/manajer dan samakan istilah.

**Hasil:** pembagian kerja dan batas modul yang dipahami kedua orang.

## Tahap 1 — Analisis kebutuhan dan aturan kas/absensi

**Bersama:** wawancara/konfirmasi alur cabang, shift, absensi, penutupan kas, laporan harian, pengguna, bukti selfie/lokasi, dan pergantian kasir.

**Hasil:** kebutuhan fungsional/nonfungsional, kriteria penerimaan, serta jawaban pertanyaan terbuka di [REQUIREMENTS.md](REQUIREMENTS.md). Selesaikan dahulu konflik laporan shift tengah dan kas saat shift tumpang tindih.

## Tahap 2 — Model proses dan rancangan

**Bersama:** buat flowchart proses berjalan/usulan, UML use case, activity/sequence untuk absensi dan tutup kas, domain/class model, ERD, kamus data, rancangan antarmuka, dan kontrak integrasi POS-pembayaran.

**Hasil:** rancangan disepakati Aurel, Syafa, serta ditinjau pembimbing/pemilik proses sebelum model data lintas modul dibuat.

## Tahap 3 — Fondasi aplikasi

**Bersama:** gunakan Django dan PostgreSQL sesuai proposal; rapikan environment lokal, konfigurasi rahasia, layout, autentikasi, hak akses, cabang, shift, dan data contoh sintetis.

**Hasil:** aplikasi lokal dapat dijalankan kedua orang dengan konfigurasi yang konsisten. Jangan mulai dengan data nyata.

## Tahap 4 — Pengerjaan modul secara terpisah

- **Aurellia:** data/penempatan karyawan, absensi masuk-pulang, izin/status, riwayat, laporan kas shift.
- **Syafa:** POS/penjualan, pembayaran, persediaan, serta laporan berkala sesuai ruang lingkup penelitiannya.
- **Bersama:** review perubahan bersama, model data inti, integrasi pembayaran, role/access, dan antarmuka lintas modul.

Setiap tugas dikerjakan di branch sendiri dan dikirim sebagai pull request. Jika kontrak data berubah, bahas sebelum implementasi.

## Tahap 5 — Integrasi

**Bersama:** hubungkan ringkasan penjualan/pembayaran Syafa ke laporan kas Aurel, satukan data cabang/shift/kasir, tangani pembatalan/retur, dan pastikan rekap hariannya tersedia setelah shift malam selesai pukul 08.00.

**Hasil:** satu alur dari transaksi pembayaran, tutup kas, sampai laporan yang dapat ditelusuri.

## Tahap 6 — Evaluasi dan perbaikan

**Bersama:** siapkan skenario Black Box memakai equivalence partitioning dan boundary value analysis; bandingkan hitung kas sistem dengan perhitungan manual pada periode/cabang yang disetujui; kumpulkan SUS 10 item skala Likert 5 poin sesuai rancangan penelitian.

Jika ada kesalahan kebutuhan atau rancangan, kembalikan temuan ke tahap terkait, perbaiki, lalu ulangi pemeriksaan pada alur yang terdampak. Simpan bukti hasil dan tindak lanjut untuk naskah.

## Tahap 7 — Persiapan operasional dan cutover

**Bersama pemilik/manajer:** inventarisasi data IPOS yang perlu diarsipkan atau dipindah, rekonsiliasi saldo awal, pelatihan, backup/restore, persiapan koneksi cabang, jadwal cutover, dan cara kembali ke proses aman jika penerapan gagal.

Sistem menggantikan IPOS setelah kesiapan dan tanggal cutover disetujui. Jangan menjalankan dua sumber transaksi operasional tanpa prosedur rekonsiliasi.

## Cara membagi kerja tiap minggu

1. Pilih tugas kecil dengan hasil dan kriteria selesai.
2. Tetapkan satu penanggung jawab utama dan satu peninjau.
3. Beri tahu rekan sebelum mengubah file/model yang dipakai bersama.
4. Buat branch tugas, commit, buka pull request, tinjau, lalu gabungkan.
5. Catat keputusan bisnis/data baru di [DECISION_LOG.md](DECISION_LOG.md).
