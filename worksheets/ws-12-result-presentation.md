# WS-12: Result Presentation & Visualization

> **Bab 12 — Penyajian Hasil & Visualisasi**

---

## Ringkasan Materi

### Data → Insight Model

```
Validated Data → Structured Presentation → Visualization → Pattern Recognition → Insight
```

Penyajian **mendahului** analisis. Tabel dan grafik membantu peneliti "melihat" data sebelum menghitung. Langsung ke uji statistik tanpa visualisasi berisiko kesimpulan yang secara teknis benar tapi kontekstual salah (Anscombe's Quartet, 1973).

### Tabel = Presisi, Grafik = Pola

Keduanya **saling melengkapi**:
- Tabel: angka presisi, self-contained (dipahami tanpa teks), sortable
- Grafik: pola visual, tren, perbandingan cepat

### Jenis Grafik Berdasarkan Tujuan

| Tujuan | Jenis Grafik |
|--------|-------------|
| Perbandingan antar-skenario | Bar chart (grouped/stacked) |
| Distribusi per-skenario | Box plot / violin plot |
| Tren temporal | Line chart |
| Korelasi dua variabel | Scatter plot |
| Proporsi (total = 100%) | Pie chart (hati-hati!) |

### Contoh Tabel Hasil yang Baik

| Model | Accuracy (%) | F1-Score (%) | Training Time (min) |
|-------|-------------|-------------|---------------------|
| BERT | 88.4 ± 1.2 | 87.1 ± 1.4 | 45.2 ± 3.1 |
| LSTM | 86.1 ± 1.8 | 84.5 ± 2.0 | 12.8 ± 1.2 |
| SVM | 82.3 ± 0.9 | 80.7 ± 1.1 | 0.3 ± 0.1 |

*N=10 per model. Mean ± std. Diurutkan berdasarkan Accuracy.*

### Visualization Bias — Yang Harus Dihindari

| Bias | Deskripsi | Dampak |
|------|----------|--------|
| Truncated axis | Y tidak dari 0 | Memperbesar perbedaan kecil |
| Inconsistent scale | Dua grafik skala beda | Perbandingan menyesatkan |
| Cherry-picked data | Hanya tampilkan yang "menang" | Selektif, tidak jujur |
| 3D effects | Efek 3D tanpa dimensi data ke-3 | Distorsi tanpa informasi |
| Missing error bar | Tidak ada variabilitas | Menyembunyikan ketidakpastian |

### Engineering vs Research Presentation

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan grafik | Dashboard monitoring | Mendukung argumen ilmiah |
| Informasi wajib | KPI, threshold | Mean, std, CI, N, p-value |
| Bias handling | Less critical | Wajib dihindari (peer-review) |

---

## Template A.12 — Result Presentation Plan

```
RESULT PRESENTATION PLAN

Research Question : Apakah manfaat yang dirasakan, kapabilitas teknologi, dan tingkat adopsi e-commerce berpengaruh terhadap peningkatan omzet UMKM bermitra Grab di Kabupaten Garut?

Metrik Utama      : 
  - Path Coefficient
  - T-Statistic
  - P-Value
  - R-Square
  - f-square

Tabel Hasil:
| Variabel | Path Coefficient (Mean ± Std) | P-Value | n |
|----------|-------------------------------:|--------:|--:|
| Manfaat yang Dirasakan → Peningkatan Omzet | 0.42 ± 0.08 | <0.001 | 98 |
| Kapabilitas Teknologi → Peningkatan Omzet | 0.35 ± 0.07 | 0.002 | 98 |
| Tingkat Adopsi E-Commerce → Peningkatan Omzet | 0.47 ± 0.09 | <0.001 | 98 |

Visualisasi yang Direncanakan:
| # | Jenis Grafik | Pesan Utama | Metrik |
|---|-------------|-------------|--------|
|---:|--------------|-------------|---------|
| 1 | Bar Chart + Error Bar | Membandingkan besarnya pengaruh setiap variabel terhadap peningkatan omzet | Path Coefficient ± Std |
| 2 | Box Plot | Menunjukkan distribusi skor jawaban responden pada setiap variabel | Nilai Likert |
| 3 | Scatter Plot | Hubungan tingkat adopsi e-commerce dengan peningkatan omzet | Skor Adopsi vs Omzet |

Bias Check:
  [ ☑ ] Y-axis mulai dari 0 (atau dijustifikasi)
  [ ☑ ] Error bar/CI ditampilkan
  [ ☑ ] Semua data disertakan (tidak cherry-picked)
  [ ☑ ] Tidak menggunakan 3D tanpa alasan
```

---

## Latihan 1 — Tabel Hasil

Buat tabel hasil eksperimen Anda (boleh dengan data simulasi jika belum punya data riil).

| Variabel | Path Coefficient (Mean ± Std) | P-Value | n |
|----------|-------------------------------:|--------:|--:|
| Tingkat Adopsi E-Commerce | 0.47 ± 0.09 | <0.001 | 98 |
| Manfaat yang Dirasakan | 0.42 ± 0.08 | <0.001 | 98 |
| Kapabilitas Teknologi | 0.35 ± 0.07 | 0.002 | 98 |

**Checklist tabel:**
- [ ☑ ] Judul, satuan, dan jumlah sampel (N) tercantum.
- [ ☑ ] Mean ± std (bukan single number).
- [ ☑ ] Diurutkan berdasarkan nilai Path Coefficient.
- [ ☑ ] Format konsisten di semua baris.

---

## Latihan 2 — Rencana Visualisasi

Rencanakan 2-3 grafik untuk menyajikan data dari Latihan 1. Setiap grafik = satu pesan.

| # | Jenis Grafik | Pesan  | Data yang Digunakan |
|---|-------------|-------|---------------------|
| 1 | Bar Chart + Error Bar | Membandingkan pengaruh ketiga variabel independen terhadap peningkatan omzet | Path Coefficient ± Std |
| 2 | Box Plot | Menampilkan penyebaran jawaban responden | Skor Likert |
| 3 | Scatter Plot | Menunjukkan hubungan tingkat adopsi e-commerce dengan peningkatan omzet | Skor Variabel X dan Y |

---

## Latihan 3 — Bias Detection

Evaluasi visualisasi berikut untuk bias (skenario dari contoh):

**Skenario:** Metode A = 91.2%, Metode B = 90.8%. Bar chart dengan Y-axis mulai dari 90%.

| Pertanyaan | Jawaban |
|-----------|---------|
| Apakah Y-axis menyesatkan? | Ya. Jika sumbu Y dimulai dari angka tinggi (misalnya 90), perbedaan kecil akan terlihat sangat besar. |
| Apakah error bar ditampilkan? | Harus ditampilkan agar variasi data terlihat. |
| Apakah semua kondisi ditampilkan? | Ya, seluruh hasil penelitian harus ditampilkan. |
| Apa solusinya? | Gunakan sumbu Y mulai dari 0, tampilkan error bar, dan sajikan seluruh data secara lengkap. |

**Evaluasi grafik Anda sendiri dari Latihan 2:**
- [ x ] Semua bias check lulus
- [ ] Ada yang perlu diperbaiki: Tidak ada. Grafik telah memenuhi prinsip visualisasi data yang baik, yaitu menggunakan sumbu Y yang sesuai, menampilkan error bar, menyajikan seluruh data, dan tidak menggunakan efek 3D yang dapat menyesatkan pembaca.

---

## Refleksi

> Mengapa tabel dan grafik keduanya diperlukan — tidak cukup salah satu saja? Pernahkah Anda membuat grafik yang (tanpa sengaja) menyesatkan?

> Tabel dan grafik memiliki fungsi yang saling melengkapi dalam penyajian hasil penelitian. Tabel menyajikan informasi numerik secara rinci sehingga memudahkan pembaca mengetahui nilai setiap indikator secara tepat. Grafik membantu pembaca memahami pola, tren, dan perbandingan antarvariabel dengan lebih cepat. Oleh karena itu, penggunaan tabel dan grafik secara bersamaan akan menghasilkan penyajian hasil penelitian yang lebih informatif, mudah dipahami, dan tetap akurat.
