# Alur Kerja Dua Pengembang

Aplikasi dikerjakan Aurellia dan Syafa bersama dalam satu repositori. Tiap orang mengerjakan modul yang menjadi tanggung jawabnya, lalu meninjau pekerjaan rekannya sebelum penggabungan.

## Branch

- main: versi yang disetujui.
- feat/aurellia-<topik>: absensi, data karyawan, laporan kas per shift.
- feat/syafa-<topik>: POS/penjualan, persediaan, laporan periode.
- docs/<topik>: UML, naskah rancangan, atau dokumentasi.

Gunakan branch dasar yang disepakati dan terbaru. Jika tim memilih branch develop sebagai tempat integrasi, tuliskan aturan tersebut sebelum dipakai. Jangan mengerjakan langsung di main.

## Siklus tugas

1. Tulis issue dengan tujuan, pemilik, dan kriteria selesai.
2. Tentukan apakah perubahan menyentuh kontrak bersama seperti cabang, shift, pembayaran, atau kas.
3. Buat branch khusus untuk satu lingkup perubahan.
4. Commit perubahan kecil dengan pesan yang mudah dipahami.
5. Buka pull request, jelaskan perubahan, file/model terdampak, dan cara rekan meninjau.
6. Rekan meninjau dan mencatat masukan.
7. Perbaiki dan gabungkan setelah kedua pihak memahami dampaknya.

## Pembagian modul dan benturan file

Aurellia terutama mengerjakan employee, attendance, dan shift_cash. Syafa terutama mengerjakan sales, inventory, dan laporan periode. Login, hak akses, cabang, shift, tanggal operasional, dan kontrak pembayaran merupakan bagian bersama.

Jika butuh mengubah model bersama, jangan membuat versi masing-masing. Buat usulan di issue atau dokumen UML, sepakati nama/relasi/aturan, lalu satu orang mengerjakan perubahan fondasi dan orang kedua meninjau.

## Lingkungan dan data

- Masing-masing komputer punya instalasi Django dan database PostgreSQL pengembangan sendiri.
- File .env berisi rahasia atau kata sandi lokal, jangan dikirim ke GitHub.
- Jangan commit database, foto selfie, lokasi, data karyawan nyata, atau data transaksi.
- Gunakan data sintetis untuk pengembangan dan dokumentasi.
- Perubahan database bersama dibagikan melalui migration Django yang ditinjau di pull request.
