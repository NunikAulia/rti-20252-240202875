# Tahap 1 — Perancangan Desain Penelitian & Variabel

**Status:** Selesai

---

## 1. Komponen Sistem

1. **Objek Penelitian** Objek penelitian adalah UMKM bermitra Grab di Kabupaten Garut yang telah memanfaatkan e-commerce dalam aktivitas pemasaran dan penjualan.
2. **Responden Penelitian**
Responden penelitian berjumlah **100 pelaku UMKM** bermitra Grab di Kabupaten Garut.
3. **Software Analisis** Pengolahan data dilakukan menggunakan **SmartPLS** dengan metode **Structural Equation Modeling - Partial Least Square (SEM-PLS)**.

## 2. Alur Penelitian

```text
Identifikasi Masalah
        │
        ▼
Studi Literatur
        │
        ▼
Penentuan Variabel Penelitian
        │
        ▼
Penyusunan Indikator & Kuesioner
        │
        ▼
Penyebaran Kuesioner
(100 Responden)
        │
        ▼
Validasi dan Pembersihan Data
        │
        ▼
Analisis Data Menggunakan SmartPLS
        │
        ▼
Interpretasi Hasil
        │
        ▼
Kesimpulan & Rekomendasi
```

---

## 3. Variabel Penelitian

| Jenis Variabel | Nama Variabel | Kode | Keterangan |
|----------------|---------------|------|------------|
| Independen | Manfaat yang Dirasakan | X1 | Persepsi pelaku UMKM terhadap manfaat penggunaan e-commerce |
| Independen | Kapabilitas Teknologi | X2 | Kemampuan pelaku UMKM dalam memanfaatkan teknologi digital |
| Independen | Tingkat Adopsi E-Commerce | X3 | Tingkat penggunaan e-commerce dalam aktivitas usaha |
| Dependen | Peningkatan Omzet UMKM | Y | Peningkatan pendapatan usaha setelah menggunakan e-commerce |
| Kontrol | Lama Usaha | K1 | Lama UMKM menjalankan usaha |
| Kontrol | Tingkat Pendidikan | K2 | Pendidikan terakhir pelaku UMKM |

---

## 4. Model Konseptual Penelitian

```text
                Manfaat yang Dirasakan (X1)
                           │
                           ▼
Kapabilitas Teknologi (X2) ───────────────►
                                           │
                                           ▼
                              Peningkatan Omzet UMKM (Y)
                                           ▲
                                           │
            Tingkat Adopsi E-Commerce (X3)
```

---

## 5. Hipotesis Penelitian

### H1
Manfaat yang dirasakan berpengaruh positif dan signifikan terhadap peningkatan omzet UMKM bermitra Grab di Kabupaten Garut.

### H2
Kapabilitas teknologi berpengaruh positif dan signifikan terhadap peningkatan omzet UMKM bermitra Grab di Kabupaten Garut.

### H3
Tingkat adopsi e-commerce berpengaruh positif dan signifikan terhadap peningkatan omzet UMKM bermitra Grab di Kabupaten Garut.

---

## 6. Struktur Data Penelitian

| Nama Kolom | Tipe Data | Keterangan |
|-------------|-----------|------------|
| ID_Responden | Integer | Nomor responden |
| X1_1 | Integer | Indikator 1 Manfaat yang Dirasakan |
| X1_2 | Integer | Indikator 2 Manfaat yang Dirasakan |
| X1_3 | Integer | Indikator 3 Manfaat yang Dirasakan |
| X2_1 | Integer | Indikator 1 Kapabilitas Teknologi |
| X2_2 | Integer | Indikator 2 Kapabilitas Teknologi |
| X2_3 | Integer | Indikator 3 Kapabilitas Teknologi |
| X3_1 | Integer | Indikator 1 Tingkat Adopsi E-Commerce |
| X3_2 | Integer | Indikator 2 Tingkat Adopsi E-Commerce |
| X3_3 | Integer | Indikator 3 Tingkat Adopsi E-Commerce |
| Y1 | Integer | Indikator 1 Peningkatan Omzet |
| Y2 | Integer | Indikator 2 Peningkatan Omzet |
| Y3 | Integer | Indikator 3 Peningkatan Omzet |
| Lama_Usaha | Integer | Lama usaha (tahun) |
| Pendidikan | Ordinal | Tingkat pendidikan responden |

---

## 7. Keputusan Teknis Penelitian

1. Pendekatan penelitian menggunakan metode kuantitatif.
2. Pengumpulan data dilakukan melalui kuesioner.
3. Skala pengukuran menggunakan skala Likert 1–5.
4. Jumlah responden sebanyak 100 UMKM.
5. Analisis data menggunakan SEM-PLS.
6. Software yang digunakan adalah SmartPLS.
7. Analisis meliputi:
   - Uji Validitas (Outer Loading, AVE)
   - Uji Reliabilitas (Composite Reliability, Cronbach's Alpha)
   - Evaluasi Inner Model (R²)
   - Path Coefficient
   - Bootstrapping
   - T-Statistic
   - P-Value
   - Effect Size (f²)
   - Predictive Relevance (Q²)

---

## Output Tahap 1

Dokumen ini menjadi dasar penyusunan instrumen penelitian, pengumpulan data, dan analisis menggunakan metode SEM-PLS pada penelitian mengenai pengaruh e-commerce terhadap peningkatan omzet UMKM bermitra Grab di Kabupaten Garut.