# Alur Kerja Dua Pengembang

## Struktur branch

- `main`: versi yang disetujui dan stabil.
- `develop`: integrasi pekerjaan yang sedang berjalan, bila tim memilih pola ini.
- `feat/aurellia-<topik>`: pekerjaan Aurellia.
- `feat/syafa-<topik>`: pekerjaan Syafa.
- `docs/<topik>`: perubahan dokumentasi/UML.

Mulai setiap tugas dari branch dasar terbaru. Hindari mengubah file yang sama tanpa koordinasi. Jika perubahan menyentuh model data bersama, tuliskan usulan terlebih dahulu lalu sepakati sebelum coding.

## Siklus perubahan

1. Buat issue/tugas dengan hasil yang diharapkan dan kriteria selesai.
2. Buat branch untuk satu lingkup kerja.
3. Kerjakan dan commit dengan pesan yang menjelaskan perubahan.
4. Buka pull request ke branch integrasi; jelaskan perubahan, dampak data, cara memeriksa, dan risiko migrasi.
5. Pengembang lain meninjau; perbaiki masukan.
6. Gabungkan setelah lolos pemeriksaan yang disepakati.
7. Integrasikan secara rutin ke lingkungan uji dengan data contoh.

## Lingkungan pengembangan

Masing-masing pengembang memakai lingkungan Python lokal dan basis data pengembangan terpisah. Jangan berbagi file SQLite yang sama lewat Git/OneDrive. Struktur environment dan cara menjalankannya akan didokumentasikan setelah stack final dipilih.

## Data dan rahasia

Gunakan data sintetis. Jangan commit `.env`, token, database berisi data nyata, file ekspor IPOS, atau data pribadi karyawan. Akses kolaborator GitHub diberikan langsung oleh pemilik repositori setelah akun Syafa diketahui dan disetujui.
