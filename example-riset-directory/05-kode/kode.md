# 05-kode

*Source code* implementasi pengolahan data — **Tahap 3 (Data Refinement Pipeline)** dan **Tahap 4 (Evaluasi Model Struktural SEM-PLS)**.

## Struktur yang direncanakan

```text
05-kode/
├── pipeline/                 # Pipeline Pembersihan & Validasi Data (Python)
│   ├── config.json           # Konfigurasi batas range skala Likert & listwise deletion
│   ├── data_refinement.py    # Skrip filter missing values & range check kuesioner
│   ├── requirements.txt      # Dependensi pustaka data (pandas, numpy, openpyxl)
│   └── run_pipeline.sh       # Skrip otomatisasi eksekusi data refinement
└── smartpls_scripts/         # Skrip Otomatisasi & Ekspor Pengujian (R/Python Wrapper)
    ├── outer_model_eval.py   # Skrip validasi konvergen, diskriminan (HTMT), & reliabilitas
    ├── inner_model_boot.py   # Skrip inferensial bootstrapping (5.000 subsamples, seed 42)
    └── export_results.py     # Skrip ekspor matriks R², f², & Path Coefficients ke (../06-output/).

## Acuan
- Protokol Pengolahan Data Awal: Laporan Log Lapangan & Prosedur Listwise Deletion (../04-data/README.md)

- Struktur Model Pengukuran & Struktural: Hasil Uji Validitas, Reliabilitas, dan Hipotesis SEM-PLS di (../06-output/).

## Deskripsi Komponen Kode

 1. Modul pipeline/
  Modul ini bertugas menangani data mentah hasil kuesioner Google Form dari 100 responden secara terprogram. Kode di dalamnya mengunci prosedur seleksi agar hanya data dengan range skor 1 hingga 5 yang lolos, serta mengeksekusi metode listwise deletion secara otomatis pada baris responden yang tidak lengkap (RESP_015 dan RESP_062) hingga menghasilkan 98 sampel bersih.

2. Modul smartpls_scripts/
 Kumpulan skrip pembungkus (wrapper) eksekusi atau pemformatan keluaran analisis statistik dari perangkat lunak SmartPLS 4.0. Skrip ini memastikan parameter pengujian berjalan secara ketat sesuai aturan riset:Penguncian nilai random seed pada angka 42 untuk menjamin aspek repeatability eksperimen.Konfigurasi penuh Complete Bootstrapping dengan 5.000 subsamples pada taraf signifikansi 5%.Otomatisasi penarikan koefisien jalur (Path Coefficient) serta pemetaan ukuran efek (Effect Size/f²) untuk dipindahkan ke folder output secara presisi.