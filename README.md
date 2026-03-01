# Proyek Akhir: Membangun Sistem Machine Learning

Repositori ini berisi berkas untuk tugas proyek akhir kelas **Membangun Sistem Machine Learning** di Dicoding. Proyek ini mendemonstrasikan end-to-end proses Machine Learning, mulai dari preprocessing dataset mentah (raw data) hingga pemodelan dan eksperimen dengan berbagai algoritma machine learning.

## Deskripsi Dataset

Dataset yang digunakan dalam proyek eksperimen ini adalah:

- **Nama**: Predict Students' Dropout and Academic Success
- **Sumber**: [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success)
- **File Lokal Mentah**: `namadataset_raw/data.csv`

Dataset ini bertujuan untuk memprediksi apakah seorang mahasiswa akan *dropout*, *enrolled* (masih berlanjut), atau lulus (*graduate*) berdasarkan berbagai parameter sosial-ekonomi dan demografis saat pendaftaran.

## Struktur Direktori

```text
Eksperimen_SML_Ahmad-Ngiliyun/
├── namadataset_raw/
│   └── data.csv                                 # Dataset mentah dari UCI ML
├── preprocessing/
│   ├── automate_Ahmad-Ngiliyun.py               # Script otomasi untuk membersihkan data & split fitur
│   ├── Eksperimen_MSML_Ahmad_Ngiliyun.ipynb     # Jupyter Notebook berisi tahapan Eksperimen Algoritma (EDA dan Model)
│   └── namadataset_preprocessing/               # (Di-generate otomatis oleh script) Berisi artefak array Numpy yang siap latih.
│       ├── feature_names.npy
│       ├── label_mapping.json
│       ├── X_test.npy
│       ├── X_train.npy
│       ├── y_test.npy
│       └── y_train.npy
└── README.md                                    # File dokumentasi proyek (ini)
```

## Cara Menjalankan Proyek

Anda bebas memilih cara untuk mengeksekusi pipeline machine learning ini menggunakan terminal atau langsung dari Jupyter Notebook.

### 1. Preprocessing Data Secara Otomatis

Anda bisa mengotomasi pemrosesan dataset mentah hanya dengan menjalankan file Python `automate_Ahmad-Ngiliyun.py`. Script ini berfungsi untuk:

- Membaca `data.csv` yang berisi delimiter `;`
- Memisahkan fitur (X) dan target label (y).
- Melakukan *One-Hot Encoding* secara otomatis pada tipe data kategorikal.
- Melabel (Encode) target kelas menjadi bentuk *integer* agar dapat dipahami model (disertai `label_mapping.json` sebagai file acuan).
- Metrik Train-Test Split (80%:20% secara bawaan/default).
- Menyimpan artefak-artefak pre-processed berwujud `.npy` (Numpy Array) di dalam `preprocessing/namadataset_preprocessing`.

Buka Terminal pada direktori root proyek dan jalankan:

```bash
cd preprocessing
python automate_Ahmad-Ngiliyun.py --input "../namadataset_raw/data.csv" --outdir "./namadataset_preprocessing" --target-col "Target"
```

*(Catatan: Anda juga bisa mengatur parameter `--drop-cols` untuk membuang fitur tertentu yang tidak diperlukan model).*

### 2. Eksperimen Model (Jupyter Notebook)

Semua tahap eksperimen utama ada pada `Eksperimen_MSML_Ahmad_Ngiliyun.ipynb`:

1. Pastikan Anda berada di virtual environment (`.venv`) dan `jupyter` telah terinstall.
2. Jalankan jupyter lab / notebook:

   ```bash
   jupyter notebook preprocessing/Eksperimen_MSML_Ahmad_Ngiliyun.ipynb
   ```

3. Di dalam *notebook* Anda akan dituntun melalui:
   - Evaluasi awal data (EDA) atau Eksplorasi Data.
   - Pemuatan preprocessed features (dari `namadataset_preprocessing`) jika menggunakan hasil skrip.
   - Pelatihan model (*Training*) dengan berbagai pendekatan algoritma machine learning dan hiperparamater untuk menemukan hasil optimal.
   - Evaluasi, penyimpanan model akhir, serta kesimpulan perolehan kinerja prediktif model.

## Lisensi & Atribusi
Proyek ini dibuat untuk keperluan edukasi dan kelulusan platform **Dicoding Indonesia**.

Lisensi kode pemrograman pada repositori ini dirilis di bawah **[MIT License](LICENSE)**.
Dibuat oleh **Ahmad Ngiliyun (@ahmadngiliyun00)**.

Hak cipta dataset mentah merujuk ke kontributor aslinya yang tertera di [sumber UCI dataset](https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success).
