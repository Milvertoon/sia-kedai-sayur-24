# Menjalankan fondasi aplikasi

Fondasi ini memakai Django 6.1.3, Python 3.12, dan SQLite sebagai pilihan awal untuk prototipe. Framework dan versi ini perlu ditinjau Aurel dan Syafa sebelum fitur transaksi mulai dibuat.

## Dengan Anaconda

1. Pasang Anaconda jika belum ada, lalu buka **Anaconda Prompt**.
2. Pindah ke folder utama repo, yaitu folder `SIA-Kedai-Sayur-24`.
3. Jalankan perintah berikut satu per satu:

```powershell
conda env create -f src/environment.yml
conda activate sia-kedai-sayur
cd src
python manage.py migrate
python manage.py runserver
```

4. Buka alamat lokal yang ditampilkan Django di browser.

Halaman saat ini hanya tampilan awal; belum ada login, karyawan, stok, penjualan, atau transaksi akuntansi.

## Tanpa Anaconda

Dengan Python 3.12 dan pip:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install -r src/requirements.txt
cd src
python manage.py migrate
python manage.py runserver
```

File database lokal `src/db.sqlite3` tidak boleh diunggah ke GitHub. Pengaturan keamanan produksi belum dibuat; jangan membuka server pengembangan untuk penggunaan toko.
