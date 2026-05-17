# WS-07: Experimental Design & Validity

> **Bab 7 — Experimental Design & Validity**

---

## Ringkasan Materi

### Correlation ≠ Causality

Kausalitas membutuhkan 3 syarat:
1. **Covariance** — X dan Y bergerak bersama
2. **Temporal precedence** — X berubah sebelum Y
3. **Elimination of alternatives** — Tidak ada faktor lain yang menjelaskan Y

Controlled experiment adalah satu-satunya metode yang bisa membuktikan kausalitas.

### Empat Jenis Validitas

| Jenis | Pertanyaan | Ancaman Umum |
|-------|-----------|-------------|
| **Internal** | Apakah hubungan IV→DV nyata? | Confounding variable, selection bias |
| **External** | Apakah bisa digeneralisasi? | Dataset terlalu spesifik |
| **Construct** | Apakah mengukur konsep yang benar? | Metrik tidak sesuai |
| **Conclusion** | Apakah kesimpulan statistik valid? | Sample size kecil, uji salah |

Internal dan external validity sering berkonflik: semakin terkontrol (internal kuat) → semakin artificial (external lemah).

### Tiga Tipe Eksperimen dalam Riset TI

| Tipe | Deskripsi | Kapan Digunakan |
|------|----------|----------------|
| **Comparison Study** | Metode A vs B pada kondisi identik | Membandingkan pendekatan berbeda |
| **Ablation Study** | Full system → lepas komponen satu per satu | Mengukur kontribusi tiap komponen |
| **Parameter Study** | Variasikan satu parameter, amati dampak | Uji sensitifitas/robustness |

### Fairness dalam Perbandingan

Perbandingan yang adil = **kondisi identik** untuk semua metode: dataset sama, preprocessing sama, tuning effort sebanding, environment sama, metrik sama.

Contoh tidak adil: Transformer (30 fitur tambahan + Bayesian optimization) vs RF (default params) → hasilnya misleading.

### Threats to Validity = Diidentifikasi Sebelum Eksperimen

Ancaman validitas harus diidentifikasi **sebelum** eksperimen dan mitigasinya dirancang sebagai bagian dari desain — bukan ditulis sebagai boilerplate setelah selesai.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan testing | Memastikan sistem memenuhi requirement | Membuktikan hubungan kausal antar variabel |
| Baseline | Versi sebelumnya (last release) | Metode tervalidasi dari literatur |
| Kegagalan | Bug → fix → release | H₀ tidak ditolak → tetap kontribusi ilmiah |
| Sukses | 100% test pass | Evidence valid — mendukung atau menolak hipotesis |

### Istilah Penting

- **Causality** — Hubungan sebab-akibat (covariance + temporal + elimination)
- **Controlled Experiment** — Ubah satu variabel, kontrol sisanya, amati efek
- **Fairness** — Semua metode diuji pada kondisi yang benar-benar identik
- **Threats to Validity** — Faktor yang bisa melemahkan kesimpulan jika tidak dimitigasi
- **Conclusion Validity** — Validitas statistik: power, sample size, uji yang tepat

---

## Template A.7 — Desain Eksperimen Lengkap

```
EXPERIMENT DESIGN

Research Question : Bagaimana pengaruh e-commerce terhadap peningkatan omzet UMKM yang bermitra dengan Grab?
Hypothesis        : E-commerce berpengaruh signifikan terhadap peningkatan omzet UMKM yang bermitra dengan Grab.
Tipe Eksperimen   : [ ✓ ] Comparison  [ ] Ablation  [ ] Parameter

Kondisi Eksperimen:
| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control   | UMKM dengan penggunaan e-commerce rendah    | Tingkat adopsi rendah      | Dataset sama, metode SEM-PLS, 100 responden |
| Treatment | UMKM dengan penggunaan e-commerce tinggi    | Tingkat adopsi tinggi      | Dataset sama, metode SEM-PLS, 100 responden |

Fairness Checklist:
  [ ✓ ] Dataset identik untuk semua kondisi
  [ ✓ ] Preprocessing setara
  [ ✓ ] Tuning effort setara
  [ ✓ ] Environment identik
  [ ✓ ] Metrik evaluasi sama

Threat Analysis:
| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal    | Bias jawaban responden | Menggunakan instrumen yang valid dan reliabel |
| External    | Sampel hanya UMKM Grab di Garut | Memperluas wilayah dan jumlah sampel |
| Construct   | Pertanyaan tidak mewakili variabel | Melakukan uji validitas dan reliabilitas |
| Conclusion  | Jumlah sampel terbatas | Menggunakan SEM-PLS dan bootstrapping |

Statistical Plan:
   Uji statistik   : SEM-PLS
   Justifikasi     : Cocok untuk penelitian kuantitatif dengan variabel laten
   Alpha           : 0,05
   Effect size min : f-square > 0,02
```

---

## Latihan 1 — Desain Eksperimen

Susun desain eksperimen berdasarkan RQ, variabel, dan sistem dari WS-04 sampai WS-06.

**RQ:** Bagaimana pengaruh e-commerce terhadap peningkatan omzet UMKM yang bermitra dengan Grab?
**Tipe eksperimen:** [ ✓ ] Comparison / [ ] Ablation / [ ] Parameter

| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control | *UMKM dengan penggunaan e-commerce rendah* | *Tingkat adopsi rendah* | *Dataset sama, metode SEM-PLS, 100 responden* |
| Treatment | *UMKM dengan penggunaan e-commerce tinggi* | *Tingkat adopsi tinggi* | *Dataset sama, metode SEM-PLS, 100 responden* |

---

## Latihan 2 — Fairness Checklist

Evaluasi apakah desain eksperimen di Latihan 1 sudah fair.

| Kriteria | Status | Detail |
|----------|--------|--------|
| Dataset identik | *✅* | Sama-sama menggunakan data UMKM mitra Grab |
| Preprocessing setara | *✅* | Data diproses dengan metode dan tahapan yang sama |
| Tuning effort setara | *✅* | Analisis menggunakan konfigurasi SEM-PLS yang sama |
| Environment identik | *✅* | Pengolahan data dilakukan pada software dan kondisi yang sama |
| Metrik evaluasi sama | *✅* | Menggunakan R-square, f-square, dan t-statistic yang sama |

**Ada yang tidak fair?** [ ] Ya / [ ✓ ] Tidak
> Tidak ada, karena seluruh kondisi eksperimen menggunakan dataset, preprocessing, metode analisis, environment, dan metrik evaluasi yang sama sehingga perbandingan eksperimen sudah fair.
---

## Latihan 3 — Threat Analysis

Identifikasi ancaman validitas untuk desain eksperimen ini.

| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal | *Bias jawaban responden pada kuesioner* | *Menggunakan instrumen yang valid dan reliabel* |
| External | *Hasil penelitian hanya berlaku untuk UMKM Grab di Garut* | *Menambah wilayah dan jumlah responden* |
| Construct | *Indikator pertanyaan tidak sesuai variabel penelitian* | *Melakukan uji validitas dan reliabilitas* |
| Conclusion | *Jumlah sampel terbatas* | *Menggunakan SEM-PLS dan bootstrapping* |

**Ancaman mana yang paling sulit dimitigasi?** External validity
**Mengapa?**
> Karena penelitian hanya menggunakan sampel UMKM mitra Grab di Kabupaten Garut sehingga hasil penelitian belum tentu dapat digeneralisasikan ke daerah lain atau jenis UMKM yang berbeda.

---

## Refleksi

> Sebuah paper melaporkan "metode kami mengalahkan semua baseline." Apa 3 pertanyaan pertama yang harus diajukan untuk mengevaluasi klaim ini?

**Jawaban:**
1. Apakah semua metode dibandingkan menggunakan dataset dan kondisi eksperimen yang sama?
2. Apakah baseline yang digunakan merupakan metode yang valid dan relevan dari literatur sebelumnya?
3. Apakah hasil pengujian didukung oleh analisis statistik dan metrik evaluasi yang valid?
