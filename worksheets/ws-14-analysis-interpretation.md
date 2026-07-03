# WS-14: Analysis, Interpretation & Failure Analysis

> **Bab 14 — Analisis Data, Interpretasi & Failure Analysis**

---

## Ringkasan Materi

### Data → Knowledge Model

```
Data → Analysis → Interpretation → Explanation → Knowledge
```

Tiga level yang berbeda:
- **Analysis** — "Apa yang terjadi?" (deskriptif + inferensial)
- **Interpretation** — "Apa artinya?" (konteks RQ + literatur)
- **Failure Analysis** — "Mengapa tidak berhasil?" (boundary conditions)

### Beyond p-value

**Statistical significance ≠ practical significance.** Selalu laporkan:
1. p-value (signifikansi statistik)
2. Effect size (besarnya efek)
3. Confidence interval (rentang ketidakpastian)

| Effect Size (Cohen's d) | Interpretasi |
|-------------------------|-------------|
| < 0.2 | Small |
| 0.2 – 0.8 | Medium |
| > 0.8 | Large |

### Pemilihan Uji Statistik

| Kondisi | Uji yang Tepat |
|---------|---------------|
| 2 grup, normal, paired | Paired t-test |
| 2 grup, non-normal | Wilcoxon signed-rank |
| > 2 grup, normal | One-way ANOVA + post-hoc |
| > 2 grup, non-normal | Kruskal-Wallis + post-hoc |
| 2 variabel kontinu | Pearson (normal) / Spearman (rank) |

### Failure Analysis as Contribution

Hipotesis yang ditolak adalah **temuan yang berharga**:

| Dataset | New (F1) | Baseline (F1) | p-value | Cohen's d |
|---------|---------|--------------|---------|-----------|
| DS-1 (small, clean) | 94.2±1.1 | 89.3±1.5 | <0.001 | **3.7** |
| DS-4 (medium, noisy) | 78.3±3.2 | 82.1±2.8 | 0.008 | **-1.3** |
| DS-5 (large, noisy) | 71.6±4.1 | 80.5±3.0 | <0.001 | **-2.5** |

**Insight:** Metode baru unggul di data bersih tapi gagal di data noisy → asumsi Gaussian dilanggar → **boundary condition** ditemukan → hybrid approach direkomendasikan.

**Partial failure + deep analysis = kontribusi lebih kaya daripada full success tanpa analisis.**

### Limitation Types

| Jenis | Contoh |
|-------|--------|
| Internal validity | Confounders yang tidak dikontrol |
| External validity | Generalisasi ke domain lain |
| Construct validity | Metrik mengukur apa yang dimaksud? |
| Statistical limitation | Sample size, asumsi distribusi |

### Jebakan Kognitif

1. "Signifikan statistik = penting secara praktis" → cek effect size
2. "Hipotesis tidak didukung → cari sudut baru" → p-hacking
3. "Kegagalan tidak perlu dilaporkan detail" → missed insight
4. "Limitasi cukup disebutkan, tidak perlu dianalisis" → kedalaman hilang

---

## Template A.14 — Analysis & Interpretation Report

```
ANALYSIS & INTERPRETATION

1. Statistik Deskriptif:
   | Skenario | Mean | Std | Median | Min | Max | n |
   |----------|------|-----|--------|-----|-----|---|
| Manfaat yang Dirasakan (X1) | 4.12 | 0.56 | 4.00 | 2 | 5 | 100 |
| Kapabilitas Teknologi (X2) | 3.95 | 0.63 | 4.00 | 2 | 5 | 100 |
| Tingkat Adopsi E-Commerce (X3) | 4.08 | 0.59 | 4.00 | 2 | 5 | 100 |
| Peningkatan Omzet (Y) | 4.01 | 0.61 | 4.00 | 2 | 5 | 100 |

2. Uji Hipotesis:
   Uji yang digunakan  : Structural Equation Modeling–Partial Least Square (SEM-PLS) dengan Bootstrapping.
   Justifikasi          : SEM-PLS dipilih karena penelitian menguji hubungan beberapa variabel laten yang diukur menggunakan skala Likert, tidak mensyaratkan distribusi normal secara ketat, serta sesuai digunakan pada sampel sebanyak 100 responden.
   Hasil: p = < 0,001, effect size (d/r/η²) = 0.41 (besar)
   CI 95%               : [0.28, 0.56]

3. Keputusan:
   [ ☑ ] H₀ ditolak → H₁ diterima
   [ ] H₀ tidak ditolak

4. Interpretasi:
   Hubungan ke RQ       : Hasil penelitian menunjukkan bahwa manfaat yang dirasakan, kapabilitas teknologi, dan tingkat adopsi e-commerce berpengaruh positif dan signifikan terhadap peningkatan omzet UMKM mitra Grab di Kabupaten Garut.
   Practical significance: Besarnya effect size menunjukkan bahwa peningkatan penggunaan teknologi digital dan e-commerce memberikan dampak nyata terhadap peningkatan omzet UMKM. Hasil ini dapat menjadi dasar bagi pelaku UMKM maupun Grab dalam meningkatkan transformasi digital usaha.
   Perbandingan literatur: Hasil penelitian konsisten dengan penelitian sebelumnya yang menyatakan bahwa persepsi manfaat teknologi, kapabilitas teknologi, dan adopsi e-commerce berpengaruh positif terhadap kinerja serta peningkatan omzet UMKM.

5. Limitation:
   | Jenis | Ancaman | Dampak | Mitigasi |
   |-------|---------|--------|----------|
   | Internal Validity | Faktor ekonomi, modal usaha, dan persaingan tidak dikontrol | Dapat memengaruhi omzet UMKM | Menambahkan variabel kontrol pada penelitian berikutnya |
   | External Validity | Sampel hanya UMKM mitra Grab Kabupaten Garut | Generalisasi terbatas | Memperluas wilayah penelitian |
   | Construct Validity | Data diperoleh melalui persepsi responden | Potensi bias jawaban | Menggunakan instrumen yang telah diuji validitas dan reliabilitas |
   | Statistical Limitation | Jumlah sampel sebanyak 100 responden | Daya generalisasi masih terbatas | Menambah jumlah responden pada penelitian selanjutnya |

6. Failure Analysis (jika H₀ tidak ditolak):
   Penyebab potensial  : Hipotesis yang tidak signifikan dapat disebabkan oleh rendahnya tingkat pemanfaatan fitur e-commerce, kemampuan teknologi pelaku UMKM yang belum merata, atau adanya faktor lain seperti modal usaha, strategi pemasaran, dan kondisi pasar yang lebih dominan memengaruhi omzet.
   Boundary condition   : Pengaruh adopsi e-commerce akan lebih besar pada UMKM yang memiliki kesiapan teknologi dan literasi digital yang baik dibandingkan UMKM yang baru mulai menggunakan platform digital.
   Insight              : Peningkatan omzet UMKM tidak hanya dipengaruhi oleh penggunaan e-commerce, tetapi juga oleh kemampuan teknologi, kesiapan digital, dan strategi bisnis yang diterapkan oleh pelaku usaha.

```

---

## Latihan 1 — Pemilihan Uji Statistik

Tentukan uji statistik yang tepat untuk eksperimen Anda.

| Pertanyaan | Jawaban |
|-----------|---------|
| Berapa grup yang dibandingkan? | 4 variabel laten (3 independen dan 1 dependen) |
| Apakah data berpasangan (paired)? | Tidak |
| Apakah distribusi normal? (uji normalitas) | Tidak menjadi syarat utama pada SEM-PLS |
| **Uji yang dipilih:** | Structural Equation Modeling–Partial Least Square (SEM-PLS) |
| **Justifikasi:** | Digunakan untuk menguji hubungan antar konstruk laten, sesuai untuk data skala Likert dan sampel sebanyak 100 responden. |

**Effect size yang akan dilaporkan:** [ ] Cohen's d / [ ] Eta-squared / [ ☑ ] Lainnya: **f², R², dan Q²**

---

## Latihan 2 — Interpretasi Hasil

Gunakan data berikut (atau data riil Anda) untuk berlatih interpretasi.

**Data:**
| Model | Accuracy (mean ± std) | n |
|-------|----------------------|---|
| A | 89.2 ± 1.5 | 10 |
| B | 87.8 ± 2.1 | 10 |

p = 0.045, Cohen's d = 0.74, CI 95% = [0.03, 2.77]

| Aspek | Interpretasi |
|-------|-------------|
| Signifikansi statistik | p = 0.045 < 0.05 sehingga terdapat perbedaan yang signifikan pada taraf signifikansi 5%. |
| Effect size | Cohen's d = 0.74 menunjukkan pengaruh sedang hingga besar (medium-to-large effect). |
| Practical significance | Model A memberikan peningkatan akurasi sekitar 1.4% dibandingkan Model B sehingga cukup bermanfaat dalam praktik. |
| Hubungan ke RQ | Hasil menunjukkan bahwa Model A lebih efektif dibandingkan Model B sehingga menjawab research question penelitian. |
| Perbandingan literatur | Hasil sejalan dengan penelitian sebelumnya yang menunjukkan bahwa model baru mampu meningkatkan performa dibandingkan model konvensional. |

---

## Latihan 3 — Failure Analysis

Latih kemampuan failure analysis: hipotesis TIDAK didukung. Apa yang bisa dipelajari?

**Skenario:** Metode baru Anda mendapat F1 = 83.2%, baseline = 84.7%. p = 0.12 (tidak signifikan).

| Pertanyaan | Jawaban |
|-----------|---------|
| Apakah ini "gagal"? | Tidak. Hipotesis yang tidak didukung tetap merupakan hasil penelitian yang valid dan dapat menjadi kontribusi ilmiah. |
| Kemungkinan penyebab? | Jumlah sampel terbatas, metode belum sesuai dengan karakteristik data, atau terdapat variabel lain yang lebih dominan memengaruhi hasil. |
| Boundary condition? | Metode lebih efektif pada kondisi data yang memenuhi asumsi model, sedangkan pada data dengan variasi tinggi metode baseline lebih stabil. |
| Insight yang bisa diambil? | Tidak semua metode baru selalu lebih baik. Karakteristik data menjadi faktor penting dalam menentukan efektivitas suatu metode. |
| Apakah layak dilaporkan? Mengapa? | Ya. Negative result memberikan informasi mengenai batas penerapan metode sehingga dapat menjadi referensi penelitian selanjutnya dan menghindari duplikasi penelitian. |

**Limitation terkait:**
| Jenis | Ancaman | Dampak |
|-------|---------|--------|
| Statistical | Sampel hanya 100 responden | Generalisasi hasil masih terbatas |
| External | Penelitian hanya dilakukan pada UMKM mitra Grab Kabupaten Garut | Hasil belum tentu berlaku pada daerah lain |
| Internal | Faktor ekonomi dan persaingan usaha tidak dikendalikan | Dapat memengaruhi peningkatan omzet UMKM |

---

## Refleksi

> Apakah "failure" dalam riset benar-benar gagal, atau justru kontribusi? Bagaimana failure analysis mengubah cara Anda melihat hasil negatif?

> Failure dalam penelitian bukan berarti penelitian gagal. Hasil yang tidak mendukung hipotesis tetap memberikan kontribusi ilmiah karena menunjukkan batas penerapan suatu teori atau model. Melalui failure analysis, peneliti dapat memahami kondisi ketika suatu pendekatan tidak bekerja secara optimal, menemukan faktor penyebabnya, serta memberikan rekomendasi yang lebih tepat untuk penelitian selanjutnya maupun implementasi di lapangan.
