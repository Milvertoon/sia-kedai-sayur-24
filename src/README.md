# Menjalankan fondasi aplikasi lokal

Fondasi ini memakai Django 6.1.3, Python 3.12, dan PostgreSQL mengikuti proposal penelitian final. PostgreSQL 15 atau lebih baru diperlukan untuk Django 6.1. Driver Python yang dipakai adalah Psycopg 3. Konfigurasi koneksi dibaca dari file .env di folder utama repo.

## Persiapan dengan VS Code dan Python

1. Pasang Python 3.12, PostgreSQL 15 atau lebih baru, dan VS Code.
2. Buka pgAdmin, lalu buat database lokal bernama sia_kedai_sayur.
3. Buka terminal PowerShell di folder utama repo.
4. Salin contoh konfigurasi [.env.example](../.env.example) menjadi .env, lalu buat virtual environment:

    copy .env.example .env
    python -m venv .venv
    .venv\Scripts\Activate.ps1
    python -m pip install -r src/requirements.txt

5. Buka file .env dan sesuaikan POSTGRES_USER serta POSTGRES_PASSWORD dengan akun PostgreSQL lokalmu. Jangan unggah file .env ke GitHub.
6. Jalankan migrasi awal dan server:

    cd src
    python manage.py migrate
    python manage.py runserver

7. Buka alamat lokal yang ditampilkan di terminal.

## Jika memakai Anaconda

Di Anaconda Prompt pada folder utama repo, buat environment dari [environment.yml](environment.yml), lalu jalankan:

    conda env create -f src/environment.yml
    conda activate sia-kedai-sayur
    copy .env.example .env
    cd src
    python manage.py migrate
    python manage.py runserver

Sebelum migrasi, sesuaikan kata sandi PostgreSQL di file .env.

Halaman saat ini hanya fondasi tampilan. Belum ada autentikasi, absensi, POS, persediaan, atau laporan kas. Jangan gunakan server pengembangan Django untuk operasional toko.
