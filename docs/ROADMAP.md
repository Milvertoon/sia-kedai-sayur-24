# Roadmap Pembangunan

Urutan berikut menjaga integrasi dua orang pada satu produk dan mencegah modul yang belum disepakati mengunci skema data terlalu dini.

## Tahap 0 — Repo dan cara kerja (selesai)

- Repo privat dan commit awal sudah ada di GitHub.
- README, `.gitignore`, aturan kolaborasi, dan pembagian awal tersedia.

## Tahap 1 — Konfirmasi kebutuhan (berjalan)

**Bersama:** tinjau [`REQUIREMENTS.md`](REQUIREMENTS.md), jawab pertanyaan bisnis, tetapkan istilah dan kriteria penerimaan.

**Hasil:** daftar kebutuhan disetujui, aktor/hak akses, aturan shift, transaksi yang sah, dan batas cutover IPOS.

## Tahap 2 — Model UML dan rancangan data

**Bersama:** buat use case, activity diagram untuk penjualan dan tutup shift, sequence diagram untuk alur transaksi penting, class/domain model, lalu ERD dan kamus data.

**Hasil:** rancangan ditinjau Aurellia dan Syafa sebelum database dibuat.

## Tahap 3 — Fondasi framework prototipe (dimulai)

Branch `feat/web-foundation` memulai Django 6.1.3, Python 3.12, SQLite, halaman awal, dan environment Anaconda. Aurel dan Syafa perlu meninjau pilihan framework/versi sebelum modul bisnis dibangun.

## Tahap 4 — Fondasi aplikasi bersama

**Bersama:** konfigurasi environment, layout, login/logout, peran, audit dasar, data toko, dan data contoh sintetis.

Perubahan model inti ditinjau kedua orang. Buat branch tugas terpisah lalu buka pull request.

## Tahap 5 — Modul operasional paralel

- **Aurellia:** karyawan, jadwal/absensi, sesi kas dan penutupan shift.
- **Syafa:** produk/pemasok, pembelian/penerimaan, kartu stok, POS dan penjualan.
- **Bersama:** sepakati kontrak integrasi penjualan–stok–kas sebelum kedua modul digabungkan.

## Tahap 6 — Akuntansi dan laporan

**Bersama, dengan Syafa mengoordinasikan laporan periode:** biaya, utang, penggajian sesuai kebutuhan yang disetujui, pemetaan akun, jurnal otomatis/manual, buku besar, neraca saldo, laba rugi, neraca, arus kas, dan laporan bulanan.

## Tahap 7 — Pemeriksaan alur dan penerimaan

**Bersama:** jalankan skenario dengan data sintetis dari login hingga laporan, rekonsiliasi stok dan kas, periksa hak akses, backup/restore, serta perbaiki temuan sebelum go-live.

## Tahap 8 — Cutover dan operasional

**Bersama:** tentukan tanggal berhenti memakai IPOS, impor/arsip data yang dibutuhkan, masukkan saldo awal, hitung stok fisik, latih pengguna, siapkan backup, dan jalankan rekonsiliasi awal.

## Ritme kerja setiap perubahan

1. Ambil satu tugas kecil yang memiliki kriteria selesai.
2. Buat branch `feat/aurellia-<topik>`, `feat/syafa-<topik>`, atau `docs/<topik>` dari branch integrasi yang disepakati.
3. Diskusikan dahulu jika mengubah model bersama atau alur lintas modul.
4. Commit, buat pull request, minta tinjauan rekan, lalu gabungkan setelah disetujui.
5. Jangan mulai dua implementasi pada file/model yang sama tanpa koordinasi.
