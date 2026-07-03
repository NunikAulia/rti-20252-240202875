# WS-13: Data Preprocessing

> **Bab 13 — Preprocessing & Persiapan Data untuk Analisis**

---

## Ringkasan Materi

### Data Refinement Pipeline

```
Raw Data → Cleaning → Transformation → Normalization → Processed Data → Analysis Ready
```

Setiap tahap memiliki tujuan berbeda. **Preprocessing bukan langkah teknis biasa** — setiap keputusan preprocessing adalah keputusan riset yang bisa mengubah kesimpulan.

### Empat Prinsip Preprocessing

| Prinsip | Deskripsi |
|---------|----------|
| **Consistency** | Metode sama untuk data yang sama |
| **Transparency** | Setiap langkah terdokumentasi |
| **Reproducibility** | Orang lain bisa mengulang dengan hasil sama |
| **Minimal Distortion** | Ubah sesedikit mungkin; jika normalisasi tidak perlu, jangan lakukan |

### Cleaning Triad

| Masalah | Strategi | Risiko |
|---------|---------|--------|
| **Missing values** | | |
| — Listwise deletion | Missing < 5%, random | Data loss |
| — Mean/median imputation | Sedikit missing, dist. normal | Mengurangi variabilitas |
| — Model-based imputation | Banyak missing, pola sistematis | Introduces dependency |
| — Flag & separate | Missing karena alasan substantif | Kompleksitas analisis |
| **Duplikat** | Identifikasi → verifikasi → hapus | False positive (data mirip ≠ duplikat) |
| **Error format** | Standardisasi tipe, encoding | Kehilangan informasi saat konversi |

### Normalisasi — Kapan & Metode Mana

| Metode | Formula | Output | Sensitif Outlier? |
|--------|---------|--------|-------------------|
| Min-max | (x-min)/(max-min) | [0, 1] | Ya |
| Z-score | (x-mean)/std | Unbounded | Lebih robust |
| Robust scaling | (x-median)/IQR | Unbounded | Paling robust |

**Kunci:** Parameter normalisasi harus dihitung dari **training set saja** — bukan seluruh data. Pelanggaran = **data leakage**.

### Data Leakage Prevention

Data leakage terjadi ketika informasi dari test set "bocor" ke preprocessing:
- Normalisasi parameter dari seluruh dataset ← **SALAH**
- Cross-validation dilakukan sebelum split ← **SALAH**
- Feature selection menggunakan label test set ← **SALAH**

### Jebakan Kognitif

1. "Preprocessing cuma teknis — tidak perlu detail" → bisa ubah kesimpulan
2. "Lebih banyak preprocessing = lebih bersih = lebih baik" → over-processing distorsi data
3. "Normalisasi selalu diperlukan" → belum tentu, tergantung metode analisis
4. "Imputation sama untuk semua situasi" → strategi harus sesuai konteks

---

## Template A.13 — Preprocessing Documentation Log

```
PREPROCESSING LOG

Dataset           : Data Kuesioner UMKM Bermitra Grab Kabupaten Garut
Jumlah data awal  : 100 responden

Cleaning:
| Masalah | Jumlah Kasus | Penanganan | Justifikasi |
|---------|-------------|------------|-------------|
| Missing Value | 2 responden | Listwise Deletion | Data tidak lengkap dan kurang dari 5% sehingga tidak memengaruhi hasil analisis |
| Data Duplikat | 0 | Tidak ada tindakan | Tidak ditemukan data ganda |
| Error Format | 3 jawaban | Konversi skala Likert menjadi numerik (1–5) | Agar data dapat diproses menggunakan SmartPLS |

Transformation:
| Transformasi | Variabel | Detail | Alasan |
|-------------|----------|--------|--------|
| Konversi Data | Semua indikator | Mengubah jawaban kuesioner menjadi angka 1–5 | Memudahkan analisis SEM-PLS |
| Coding | Variabel Demografi | Pendidikan dan lama usaha dikodekan menjadi numerik | Mempermudah pengolahan data |

Normalization:
  Metode    : Tidak dilakukan
  Alasan    : Data menggunakan skala Likert yang telah memiliki rentang seragam (1–5), sehingga tidak memerlukan normalisasi pada analisis SEM-PLS.
  Parameter : Tidak diperlukan.

Leakage Check:
  [ ☑ ] Parameter normalisasi dari training set saja
  [ ☑ ] Tidak ada informasi test set dalam preprocessing
  [ ☑ ] Cross-validation dilakukan setelah split

Jumlah data akhir : 98 responden
Script tersedia   : [ ] Ya → path: ____ | [ ☑ ] Belum
```

---

## Latihan 1 — Cleaning Plan

Periksa dataset Anda (atau dataset contoh) dan dokumentasikan masalah yang ditemukan.

| Masalah | Jumlah Kasus | Penanganan | Justifikasi |
|---------|-------------|------------|-------------|
| Missing pada jawaban kuesioner | 2 dari 100 | Listwise deletion | Missing <5% dan bersifat acak |
| Duplikat data | 0 | Tidak ada | Tidak ditemukan responden ganda |
| Error input skala | 3 | Standarisasi menjadi skala 1–5 | Menjaga konsistensi data |

**Jumlah data sebelum cleaning:** 100
**Jumlah data setelah cleaning:** 98
**Persentase data yang hilang/berubah:** 2%

---

## Latihan 2 — Normalisasi Decision

Tentukan apakah data Anda perlu normalisasi, dan jika ya, metode apa yang tepat.

| Variabel | Range Asli | Distribusi | Outlier? | Metode Normalisasi | Alasan |
|----------|-----------|-----------|----------|-------------------|--------|
| Manfaat yang Dirasakan | 1–5 | Hampir Normal | Tidak | Tidak perlu | Skala Likert |
| Kapabilitas Teknologi | 1–5 | Hampir Normal | Tidak | Tidak perlu | Skala sama |
| Tingkat Adopsi E-Commerce | 1–5 | Hampir Normal | Tidak perlu | Tidak | Skala sama |
| Peningkatan Omzet | 1–5 | Hampir Normal | Tidak | Tidak perlu | Variabel laten SEM-PLS |

**Apakah normalisasi diperlukan?** [  ] Ya / [ ☑ ] Tidak
**Justifikasi:**
> Seluruh indikator penelitian menggunakan skala Likert 1–5 dengan rentang yang sama. Analisis menggunakan SEM-PLS juga tidak mensyaratkan normalisasi data sehingga normalisasi tidak dilakukan.

**Leakage check:**
- [ ☑ ] Parameter dihitung hanya dari data penelitian.
- [ ☑ ] Tidak ada proses normalisasi setelah train-test split karena penelitian tidak menggunakan model prediksi berbasis training dan testing.

---

## Latihan 3 — Preprocessing Report

Buat ringkasan preprocessing lengkap — dokumentasi yang cukup bagi orang lain untuk mereplikasi.

```
PREPROCESSING SUMMARY

1. Dataset: Data Kuesioner UMKM Bermitra Grab Kabupaten Garut.
2. Data awal: 100 records, 4 features
3. Cleaning:
   - Missing values: 2 kasus, metode: Listwise deletion.
   - Duplikat: 0 kasus, tindakan: tidak ada
   - Error: 3 kasus, tindakan: Standarisasi skala Likert menjadi numerik.
4. Transformation: Konversi jawaban kuesioner menjadi data numerik serta pemberian kode pada variabel kategori.
5. Normalisasi: tidak diperlukan, parameter dari: Tidak ada
6. Data akhir: 98 records, 4 features
7. Leakage check: [ ☑ ] Lulus / [ ] Ada masalah
```

---

## Refleksi

> Apakah Anda pernah melakukan normalisasi "karena biasa dilakukan" tanpa mempertimbangkan apakah benar-benar diperlukan? Apa risiko over-preprocessing?

> > Normalisasi tidak selalu diperlukan dalam setiap penelitian. Pada penelitian ini, data menggunakan skala Likert 1–5 dengan rentang yang sama dan dianalisis menggunakan metode SEM-PLS sehingga normalisasi tidak diperlukan. Over-preprocessing dapat mengubah karakteristik asli data, mengurangi interpretasi terhadap jawaban responden, serta berpotensi memengaruhi hasil analisis dan kesimpulan penelitian.
