# WS-05: Variabel & Metrik

> **Bab 5 — Metric, Measurement & Data**

---

## Ringkasan Materi

### Measurement Alignment Model

Setiap pengukuran yang valid harus bisa ditelusuri melalui rantai ini tanpa lompatan logis:

```
Problem → Concept → Variable → Metric → Data → Result
```

### Operationalization = Keputusan Desain

Menerjemahkan konsep abstrak menjadi variabel terukur bukan proses mekanis. "Code quality" yang diukur via SonarQube code smells membawa asumsi implisit. Setiap operasionalisasi harus didokumentasikan dan dijustifikasi.

### Empat Tipe Data (NOIR)

| Tipe | Ciri | Contoh | Operasi Valid |
|------|------|--------|---------------|
| **Nominal** | Kategori, tanpa urutan | Jenis algoritma (RF, SVM, CNN) | Modus, chi-square |
| **Ordinal** | Urutan, interval tidak sama | Skala Likert (1-5) | Median, Spearman |
| **Interval** | Jarak bermakna, tanpa nol absolut | Suhu Celsius | Mean, Pearson, t-test |
| **Ratio** | Jarak bermakna + nol absolut | Waktu eksekusi (ms) | Semua operasi |

Tipe data menentukan uji statistik yang valid. Kebanyakan metrik performa TI = ratio; persepsi pengguna = ordinal.

### Kriteria Pemilihan Metrik

- **Representative** — Mewakili konsep yang diteliti
- **Sensitive** — Cukup peka menangkap perbedaan bermakna (hindari ceiling effect)
- **Feasible** — Bisa dikumpulkan dalam batasan waktu dan biaya

### Pre-registration

Metrik harus ditentukan **sebelum** eksperimen. Memilih metrik setelah melihat data = **p-hacking**. Metrik tambahan yang ditemukan kemudian dilaporkan sebagai *exploratory*, bukan *confirmatory*.

### Primary vs Secondary Metric

- **Primary Metric** — Langsung terikat ke hipotesis, menentukan kesimpulan
- **Secondary Metric** — Pendukung, dilaporkan di samping primary; statusnya suplementer

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Pemilihan metrik | Berdasarkan kebiasaan/tool yang ada | Berdasarkan construct validity |
| Anomali | Dihapus untuk laporan bersih | Diinvestigasi — bisa jadi temuan |
| Kapan dipilih | Setelah sistem jadi (monitoring) | Sebelum eksperimen (by design) |

### Istilah Penting

- **Operationalization** — Transformasi konsep abstrak menjadi variabel terukur
- **Construct Validity** — Sejauh mana pengukuran benar-benar mengukur konsep yang dimaksud
- **Measurement Scale** — Klasifikasi data (NOIR) yang menentukan analisis valid
- **Multi-metric Evaluation** — Menggunakan beberapa metrik untuk menangkap konsep kompleks

---

## Template A.5 — Definisi Variabel, Metrik & Justifikasi

```
VARIABLE & METRIC DEFINITION

Research Question: Apakah manfaat yang dirasakan, kapabilitas teknologi, dan tingkat adopsi e-commerce berpengaruh signifikan terhadap peningkatan omzet UMKM bermitra GRAB di Kabupaten Garut menggunakan metode SEM-PLS?

| Variabel | Tipe | Konsep | Metrik | Skala | Satuan | Cara Mengukur | Justifikasi |
|----------|------|--------|--------|-------|--------|---------------|-------------|
| Manfaat yang dirasakan | IV | Persepsi manfaat penggunaan e-commerce | Skor kuesioner Likert | Ordinal | Skor | Menggunakan kuesioner skala Likert 1–5 | Mengukur sejauh mana UMKM merasakan manfaat e-commerce |
| Kapabilitas teknologi | IV | Kemampuan penggunaan teknologi digital | Skor kuesioner Likert | Ordinal | Skor | Menggunakan kuesioner skala Likert 1–5 | Menilai kemampuan UMKM dalam menggunakan teknologi |
| Tingkat adopsi e-commerce | IV | Tingkat penerapan e-commerce | Skor kuesioner Likert | Ordinal | Skor | Menggunakan kuesioner skala Likert 1–5 | Mengukur tingkat penggunaan e-commerce pada UMKM |
| Peningkatan omzet | DV | Kenaikan pendapatan usaha | R-Square, Path Coefficient, T-Statistic, P-Value | Ratio | Nilai statistik | Analisis menggunakan SEM-PLS | Mengukur pengaruh variabel e-commerce terhadap omzet |
| Lama usaha | CV | Pengalaman usaha | Lama usaha dalam tahun | Ratio | Tahun | Data identitas responden | Mengontrol pengaruh pengalaman usaha |
| Pendidikan terakhir | CV | Tingkat pendidikan pelaku usaha | Jenjang pendidikan | Ordinal | Tingkat | Data identitas responden | Mengontrol pengaruh pendidikan terhadap penggunaan teknologi |

Alignment Check:
  RQ → Concept → Variable → Metric → Data → Result
  [ ✓ ] Setiap langkah terdokumentasi
  [ ✓ ] Tidak ada "lompatan logis"
  [ ✓ ] Metrik mengukur apa yang dimaksud (construct validity)
```

---

## Latihan 1 — Operationalization Chain

Gunakan RQ dari WS-04. Definisikan variabel dan metriknya.

**RQ:** Apakah manfaat yang dirasakan, kapabilitas teknologi, dan tingkat adopsi e-commerce berpengaruh signifikan terhadap peningkatan omzet UMKM bermitra GRAB di Kabupaten Garut?

| Variabel | Tipe | Konsep Abstrak | Metrik Konkret | Skala (NOIR) | Satuan |
|----------|------|---------------|----------------|-------------|--------|
| *Manfaat yang dirasakan* | *IV* | *Persepsi manfaat e-commerce* | *Skor Likert 1–5* | *Ordinal* | *Skor* |
| *Kapabilitas teknologi*| *IV* | *Kemampuan teknologi digital* | *Skor Likert 1–5* | *Ordinal* | *Skor* |
| *Tingkat adopsi e-commerce* | *IV* | *Tingkat penggunaan e-commerce* | *Skor Likert 1–5* | *Ordinal* | *Skor* |
| *Peningkatan omzet* | *DV* | *Kenaikan pendapatan usaha* | *R-Square, T-Statistic, P-Value* | *Ratio* | *Nilai statistik* |
| *Lama usaha* | *CV* | *Pengalaman menjalankan usaha* | *Lama usaha* | *Ratio* | *Tahun* |
| *Pendidikan terakhir* | *CV* | *Tingkat pendidikan* | *Jenjang pendidikan* | *Ordinal* | *Tingkat* |

**Apakah ada lompatan logis dalam rantai?** [ ] Ya / [ ✓ ] Tidak
> Jika ya, di mana? Tidak ada, karena seluruh konsep abstrak sudah diterjemahkan menjadi variabel yang dapat diukur secara statistik.

---

## Latihan 2 — Evaluasi Metrik

Evaluasi metrik DV yang dipilih di Latihan 1 menggunakan 3 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Representative | *5* | *Metrik SEM-PLS mampu merepresentasikan hubungan antar variabel penelitian* |
| Sensitive | *4*| *Metrik cukup sensitif dalam mendeteksi perubahan pengaruh antar variabel* |
| Feasible | *5* | *Data mudah diperoleh melalui penyebaran kuesioner kepada responden UMKM* |

**Apakah perlu secondary metric?** [ ✓ ] Ya / [ ] Tidak
> Jika ya, apa dan mengapa? Ya, menggunakan Cronbach Alpha dan Composite Reliability untuk mendukung validitas dan reliabilitas instrumen penelitian.

**Contoh kasus ceiling effect untuk metrik ini:**
> Jika hampir seluruh responden memberikan skor sangat tinggi pada penggunaan e-commerce, maka variasi data menjadi kecil sehingga pengaruh antar variabel sulit dibedakan secara signifikan.

---

## Latihan 3 — Data Quality Check

Bayangkan data yang akan dikumpulkan dari eksperimen. Evaluasi 4 dimensi kualitas data.

| Dimensi | Pertanyaan | Jawaban | Strategi Mitigasi |
|---------|-----------|---------|------------------|
| Completeness | *Apakah semua data point terkumpul?* | *Sebagian besar data lengkap* | *Memastikan seluruh kuesioner diisi lengkap sebelum analisis* |
| Consistency | *Apakah ada kontradiksi internal?* | *Ada kemungkinan jawaban tidak konsisten* | *Melakukan pengecekan dan validasi data* |
| Validity | *Apakah benar-benar mengukur yang dimaksud?* | *Ya, menggunakan indikator berdasarkan teori dan uji validitas* | *Menggunakan indikator variabel yang sesuai literatur* |
| Representativeness | *Apakah sampel mewakili populasi target?* | *Ya, responden berasal dari UMKM mitra GRAB* | *Menggunakan teknik sampling sesuai rumus Slovin* |

---

## Refleksi

> Mengapa memilih metrik setelah melihat data dianggap p-hacking? Apa bedanya dengan eksplorasi data yang sah?

**Jawaban:**
> Memilih metrik setelah melihat data dianggap p-hacking karena peneliti dapat memilih hasil yang terlihat paling signifikan sehingga kesimpulan penelitian menjadi bias dan tidak objektif.

> Berbeda dengan eksplorasi data yang sah, eksplorasi dilakukan untuk memahami pola data tanpa mengubah hipotesis utama atau memanipulasi hasil penelitian yang telah ditentukan sebelum eksperimen dilakukan.
