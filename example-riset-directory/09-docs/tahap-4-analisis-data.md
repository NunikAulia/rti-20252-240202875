# Tahap 4 - Validasi Data dan Analisis SEM-PLS

**Status:** Selesai  
**Bergantung pada:** Tahap 3 - Pengumpulan Data Kuesioner

---

## Tujuan

Mengolah data hasil kuesioner dari 100 pelaku UMKM mitra Grab di Kabupaten Garut menggunakan metode **Structural Equation Modeling - Partial Least Squares (SEM-PLS)** dengan bantuan aplikasi **SmartPLS**.

Tahap ini bertujuan untuk menguji kualitas data, validitas dan reliabilitas instrumen penelitian, serta hubungan antar variabel yang telah dirumuskan pada hipotesis penelitian.

---

## Deliverable

- Dataset hasil kuesioner (.xlsx)
- Data responden yang telah divalidasi
- Model penelitian pada SmartPLS
- Hasil evaluasi Outer Model
- Hasil evaluasi Inner Model
- Hasil Bootstrapping
- Hasil pengujian hipotesis
- Ringkasan hasil analisis

---

# Variabel Penelitian

| Variabel | Kode | Jenis |
|----------|------|--------|
| Manfaat yang Dirasakan | X1 | Independen |
| Kapabilitas Teknologi | X2 | Independen |
| Tingkat Adopsi E-Commerce | X3 | Independen |
| Peningkatan Omzet UMKM | Y | Dependen |

---

# Alur Analisis

```text
Data Kuesioner
      │
      ▼
Validasi Data
      │
      ▼
Input ke SmartPLS
      │
      ▼
Menyusun Model SEM-PLS
      │
      ▼
Evaluasi Outer Model
      │
      ▼
Evaluasi Inner Model
      │
      ▼
Bootstrapping
      │
      ▼
Uji Hipotesis
      │
      ▼
Interpretasi Hasil
```

---

# Validasi Data

Tahap awal dilakukan pemeriksaan terhadap data yang diperoleh dari kuesioner.

| Komponen | Hasil |
|----------|--------|
| Jumlah Responden | 100 |
| Data Lengkap | 100 |
| Data Tidak Lengkap | 0 |
| Data Valid | 100 |
| Skala Pengukuran | Likert 1–5 |

Data yang telah memenuhi persyaratan selanjutnya diolah menggunakan SmartPLS.

---

# Evaluasi Outer Model

Evaluasi Outer Model bertujuan menguji validitas dan reliabilitas indikator pada setiap konstruk penelitian.

## Kriteria Pengujian

| Pengujian | Nilai Minimum |
|------------|--------------|
| Outer Loading | ≥ 0,70 |
| Average Variance Extracted (AVE) | ≥ 0,50 |
| Composite Reliability | ≥ 0,70 |
| Cronbach's Alpha | ≥ 0,70 |

## Hasil Evaluasi

| Variabel | Outer Loading | AVE | Composite Reliability | Cronbach Alpha | Keterangan |
|----------|---------------|-----|----------------------|----------------|------------|
| X1 | Memenuhi | Memenuhi | Memenuhi | Memenuhi | Valid |
| X2 | Memenuhi | Memenuhi | Memenuhi | Memenuhi | Valid |
| X3 | Memenuhi | Memenuhi | Memenuhi | Memenuhi | Valid |
| Y | Memenuhi | Memenuhi | Memenuhi | Memenuhi | Valid |

---

# Evaluasi Inner Model

Evaluasi Inner Model dilakukan untuk mengetahui kekuatan hubungan antar variabel.

## Pengujian

| Analisis | Fungsi |
|----------|---------|
| R-Square | Menjelaskan kemampuan variabel independen terhadap variabel dependen |
| Path Coefficient | Menentukan arah hubungan antar variabel |
| Effect Size (f²) | Mengukur besar pengaruh masing-masing variabel |
| Predictive Relevance (Q²) | Mengukur kemampuan prediksi model |
| Bootstrapping | Menguji signifikansi hubungan antar variabel |

---

# Pengujian Hipotesis

Kriteria pengambilan keputusan:

- T-Statistic > 1,96
- P-Value < 0,05

## Hasil Pengujian

| Hipotesis | Hubungan Variabel | Keputusan |
|------------|-------------------|-----------|
| H1 | X1 → Y | Diuji |
| H2 | X2 → Y | Diuji |
| H3 | X3 → Y | Diuji |

---

# Interpretasi

Berdasarkan hasil analisis SEM-PLS, hubungan antar variabel dinilai melalui nilai Path Coefficient, T-Statistic, dan P-Value.

Hipotesis diterima apabila:

- T-Statistic > 1,96
- P-Value < 0,05

Hipotesis ditolak apabila:

- T-Statistic ≤ 1,96
- P-Value ≥ 0,05

---

# Output Tahap 4

- Data responden tervalidasi
- Model SEM-PLS
- Nilai Outer Loading
- Nilai AVE
- Nilai Composite Reliability
- Nilai Cronbach Alpha
- Nilai R-Square
- Nilai Effect Size (f²)
- Nilai Q²
- Nilai Path Coefficient
- Nilai T-Statistic
- Nilai P-Value
- Kesimpulan hasil pengujian hipotesis

---

# Persiapan Tahap 5

Output dari tahap ini digunakan sebagai dasar penyusunan:

1. Bab Hasil Penelitian
2. Bab Pembahasan
3. Kesimpulan
4. Rekomendasi penelitian
5. Artikel ilmiah/jurnal