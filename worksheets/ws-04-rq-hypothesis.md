# WS-04: Research Question & Hypothesis

> **Bab 4 — Research Question, Contribution & Hypothesis**

---

## Ringkasan Materi

### RQ Bukan Pertanyaan Biasa

Research Question yang baik secara implisit mengandung cetak biru eksperimen: subjek, baseline, metrik, domain, dataset.

| Kualitas | Contoh |
|----------|--------|
| **Buruk** | "Bagaimana pengaruh deep learning terhadap deteksi malware?" |
| **Baik** | "Apakah CNN menghasilkan F1-Score lebih tinggi dari RF pada CIC-MalMem-2022?" |

Perbedaan: RQ yang baik menyebutkan **metode spesifik**, **metrik terukur**, **baseline**, dan **dataset**.

### Tiga Jenis RQ

| Jenis | Pola | Kebutuhan |
|-------|------|-----------|
| **Comparison** | A vs B → mana lebih baik? | ≥ 2 metode, metrik sama |
| **Improvement** | A' vs A → modifikasi lebih baik? | Pre/post, bukti perbaikan |
| **Exploratory** | Faktor X₁...Xₙ → pengaruh terhadap Y? | Multi-variabel, korelasi/regresi |

### Contribution Statement

Tiga jenis kontribusi: **Improvement** (metode terbukti lebih baik), **Comparison** (perbandingan sistematis yang belum ada), **Novel Approach** (pendekatan baru). Kontribusi harus terhubung langsung dengan gap — kontribusi tanpa gap = klaim tanpa justifikasi.

### Hypothesis H₀ / H₁

- **H₀** (Null) = Tidak ada perbedaan signifikan — asumsi default, harus dibuktikan salah
- **H₁** (Alternative) = Ada perbedaan signifikan — diterima hanya jika H₀ ditolak
- Harus **falsifiable**, mengandung **metrik terukur**, dirumuskan **SEBELUM eksperimen**

### Rantai Operasionalisasi

```
RQ → Variable → Metric → Data → Analysis
```

Jika rantai ini tidak lengkap, RQ belum mature. Bi-directional: RQ yang tidak bisa jadi hipotesis testable harus direvisi mundur.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan pertanyaan | Apa yang harus dibangun? | Apa yang harus dibuktikan? |
| Bentuk jawaban | Sistem yang berfungsi | Bukti empiris terukur |
| Sukses diukur oleh | User satisfaction, uptime | Signifikansi statistik, effect size |
| Jika gagal | Debug dan perbaiki | Laporkan, analisis mengapa |

### Istilah Penting

- **Research Question (RQ)** — Pertanyaan spesifik: variabel terukur + metrik + konteks
- **Contribution Statement** — Apa yang diketahui setelah riset selesai yang sebelumnya belum ada
- **H₀ / H₁** — Null vs Alternative Hypothesis
- **Falsifiability** — Kondisi hipotesis ditolak harus bisa didefinisikan sebelum eksperimen
- **Operationalization** — Proses mewujudkan konsep abstrak menjadi variabel terukur

---

## Template A.4 — RQ-Contribution-Hypothesis

```
RQ-CONTRIBUTION-HYPOTHESIS

Gap Statement  : ____________________

Research Question:
  Tipe         : [ ] Comparison  [ ] Improvement  [ ✓ ] Exploratory
  Formulasi    :  Apakah manfaat yang dirasakan, kapabilitas teknologi, dan tingkat adopsi e-commerce berpengaruh signifikan terhadap peningkatan omzet UMKM bermitra GRAB di Kabupaten Garut menggunakan metode SEM-PLS?
  Variabel IV  : 1. Manfaat yang dirasakan
                  2. Kapabilitas teknologi
                  3. Tingkat adopsi e-commerce
  Variabel DV  : Peningkatan omzet UMKM
  Metrik       : R-Square, Path Coefficient, T-Statistic, P-Value, dan f-square
  Dataset      : Data primer dari 100 responden UMKM bermitra GRAB di Kabupaten Garut
  Baseline     : Penelitian terdahulu mengenai pengaruh e-commerce terhadap UMKM

Quality Check RQ:
  [ ✓ ] Variabel spesifik
  [ ✓ ] Metrik jelas
  [ ✓ ] Baseline ada
  [ ✓ ] Konteks disebutkan
  [ ✓ ] Memerlukan eksperimen (bukan hanya survei literatur)

Contribution Statement:
  Apa yang baru diketahui :   Penelitian ini menunjukkan bahwa penggunaan e-commerce memiliki pengaruh signifikan terhadap peningkatan omzet UMKM, terutama pada aspek kapabilitas teknologi.

  Jenis kontribusi        : [ ] Improvement  [ ] Comparison  [ ✓ ] Novel approach
  Gap yang diisi          :   Kurangnya penelitian spesifik mengenai pengaruh e-commerce terhadap peningkatan omzet UMKM mitra GRAB menggunakan metode SEM-PLS.

Hypothesis Pair:
  H₀ :  Tidak terdapat pengaruh signifikan antara manfaat yang dirasakan, kapabilitas teknologi, dan tingkat adopsi e-commerce terhadap peningkatan omzet UMKM bermitra GRAB di Kabupaten Garut.

  H₁ : Terdapat pengaruh signifikan antara manfaat yang dirasakan, kapabilitas teknologi, dan tingkat adopsi e-commerce terhadap peningkatan omzet UMKM bermitra GRAB di Kabupaten Garut.

  Threshold              : P-Value < 0,05 dan T-Statistic > 1,96
  Justifikasi threshold  :   Threshold tersebut merupakan standar umum pengujian signifikansi statistik pada metode SEM-PLS.
```

---

## Latihan 1 — Dari Gap ke RQ

Gunakan gap yang ditemukan di WS-03. Transformasikan menjadi Research Question.

**Gap dari WS-03:** Masih sedikit penelitian yang membahas pengaruh e-commerce terhadap peningkatan omzet UMKM mitra GRAB menggunakan pendekatan SEM-PLS.

**RQ versi pertama (tulis bebas):**
> Bagaimana pengaruh e-commerce terhadap peningkatan omzet UMKM?


**Evaluasi RQ:**

| Komponen | Ada? | Isi |
|----------|------|-----|
| Metode spesifik | *Ya* | SEM-PLS |
| Metrik terukur | *Ya* | R-Square, T-Statistic, P-Value |
| Baseline | *Ya* | Penelitian terdahulu e-commerce UMKM |
| Dataset/konteks | *Ya* | UMKM mitra GRAB Kabupaten Garut |

**Tipe RQ:** [ ] Comparison / [ ] Improvement / [ ✓ ] Exploratory

**RQ versi revisi (setelah evaluasi):**
> Apakah manfaat yang dirasakan, kapabilitas teknologi, dan tingkat adopsi e-commerce berpengaruh signifikan terhadap peningkatan omzet UMKM bermitra GRAB di Kabupaten Garut menggunakan metode SEM-PLS?

---

## Latihan 2 — Hypothesis Pair

Rumuskan pasangan hipotesis dari RQ di Latihan 1.

| Komponen | Isi |
|----------|-----|
| H₀ | *Tidak ada pengaruh signifikan e-commerce terhadap peningkatan omzet UMKM* |
| H₁ | *Ada pengaruh signifikan e-commerce terhadap peningkatan omzet UMKM* |
| Metrik | *T-Statistic, P-Value, R-Square* |
| Threshold | *P-Value < 0,05* |
| Justifikasi threshold | *Digunakan sebagai standar signifikansi statistik dalam SEM-PLS* |

**Apakah hipotesis ini falsifiable?** [ ✓ ] Ya / [ ] Tidak
> Bagaimana cara membuktikannya salah? Hipotesis dapat ditolak apabila hasil pengujian menunjukkan nilai P-Value > 0,05 atau nilai T-Statistic < 1,96.


---

## Latihan 3 — Rantai Operasionalisasi

Lengkapi rantai dari RQ hingga metode analisis.

| Tahap | Isi |
|-------|-----|
| RQ | *Apakah e-commerce berpengaruh terhadap peningkatan omzet UMKM mitra GRAB?* |
| Variable (IV) | *Manfaat yang dirasakan, kapabilitas teknologi, tingkat adopsi* |
| Variable (DV) | *Peningkatan omzet* |
| Metric | *R-Square, Path Coefficient, T-Statistic, P-Value* |
| Data source | *Kuesioner 100 responden UMKM mitra GRAB* |
| Analysis method | *SEM-PLS* |

**Apakah rantai lengkap?** [ ✓ ] Ya / [ ] Tidak
> Jika tidak, tahap mana yang perlu direvisi? Tidak perlu revisi karena semua komponen sudah lengkap.

---

## Refleksi

> Ambil satu judul skripsi/paper yang pernah dibaca. Coba ekstrak RQ-nya. Apakah RQ tersebut memenuhi semua komponen (metode, metrik, baseline, konteks)? Jika tidak, apa yang hilang?

**Judul:** Pengaruh E-Commerce Terhadap Peningkatan Omzet UMKM Bermitra Grab di Kabupaten Garut

**RQ yang diekstrak:** Apakah penggunaan e-commerce berpengaruh signifikan terhadap peningkatan omzet UMKM bermitra GRAB di Kabupaten Garut?

**Komponen yang hilang:** Tidak ada, karena penelitian sudah memiliki metode, metrik, variabel, dataset, dan analisis yang jelas.


