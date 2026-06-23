# WS-11: Data Validation & Integrity

> **Bab 11 — Validasi Data & Integritas**

---

## Ringkasan Materi

### Data Trust Model

```
Raw Data → Data Cleaning → Consistency Check → Validation Process → Trusted Data
```

Data mentah belum bisa dipercaya. Harus melewati pipeline validasi sebelum siap untuk analisis statistik.

### Empat Pilar Data Quality

| Pilar | Deskripsi | Contoh Pelanggaran |
|-------|----------|-------------------|
| **Accuracy** | Nilai dalam range masuk akal | Akurasi = 1.5 (di luar [0,1]) |
| **Consistency** | Format seragam di semua run | Run 1: CSV, Run 2: JSON |
| **Completeness** | Tidak ada data hilang dari plan | 97 dari 100 run tercatat |
| **Validity** | Data sesuai desain eksperimen | Parameter baseline tercampur treatment |

### Proses Validasi Progresif

1. **Format validation** — Tipe file, header, kolom
2. **Range validation** — Nilai dalam batas logis
3. **Consistency validation** — Format seragam antar-run
4. **Logic validation** — Data cocok dengan desain eksperimen

Jika gagal di langkah awal → tidak perlu lanjut.

### Anomaly Detection — 3 Jenis

| Jenis | Deskripsi | Deteksi |
|-------|----------|---------|
| **Statistical outlier** | Nilai di luar distribusi normal | IQR: < Q1-1.5×IQR atau > Q3+1.5×IQR |
| **Contextual anomaly** | Normal absolut, abnormal dalam konteks | Run 1-10: ~91%, Run 11-20: ~88% |
| **Pattern anomaly** | Pola sistematis (bukan random) | Performa menurun berurutan |

**Prinsip:** Detect → Investigate → Document → Decide — **JANGAN langsung hapus.**

### Engineering vs Research Validation

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Data sesuai spesifikasi bisnis | Data layak untuk analisis statistik |
| Missing data | Impute / set default | Investigasi penyebab → dokumentasi |
| Outlier | Bug → fix | Mungkin temuan → investigasi |
| Dokumentasi | Minimal (log error) | Komprehensif (anomali + keputusan) |

### Jebakan Kognitif

1. "Logging otomatis ≠ data benar" → bisa ada bug di logger
2. "Outlier = hapus" → bisa jadi temuan penting
3. "Dataset kecil tidak perlu validasi" → justru lebih rentan
4. "Mean normal = data benar" → [94, 95, 93, **44**, 94] → mean 84% terlihat wajar

---

## Template A.11 — Data Validation Checklist

```
DATA VALIDATION CHECKLIST

Completeness:
  [ ☑ ] Semua skenario tercakup
  [ ☑ ] Jumlah run sesuai rencana
  [ ☑ ] Tidak ada file output hilang
  Missing: 0 dari 100 data responden

Format Consistency:
  [ ☑ ] Semua file format sama (CSV/JSON/Excel)
  [ ☑ ] Header konsisten
  [ ☑ ] Tipe data konsisten (numerik tetap numerik)

Range & Logic:
  [ ☑ ] Nilai dalam range masuk akal
  [ ☑ ] Tidak ada waktu negatif
  [ ☑ ] Metrik 0–100%, tidak di luar range
  Anomali ditemukan: Tidak ditemukan anomali signifikan pada tahap validasi awal.

Cross-Validation:
  [ ☑ ] Run identik → hasil mendekati
  [ ☑ ] Trend konsisten dengan ekspektasi teori

Keputusan:
  [ ☑ ] Data siap analisis
  [ ] Perlu cleaning
  [ ] Perlu re-run (skenario: ____)
```

---

## Latihan 1 — Completeness Check

Verifikasi apakah semua data yang direncanakan sudah terkumpul.

| Skenario | Run Direncanakan | Run Tercatat | Missing | Alasan |
|----------|-----------------|-------------|---------|--------|
| Penyebaran Kuesioner	| 100	| 100	| 0	| - |
| Pemeriksaan Data	| 100	| 100	| 0	| - |
| Uji Validitas	| 100	| 100	| 0	| - |
| Uji Reliabilitas	| 100	| 100	| 0	| - |
| Analisis SEM-PLS	| 100 |	100	| 0	| - |

**Total expected:** 100 | **Total actual:** 100 | **Missing:** 0

**Keputusan untuk data missing:**
> Tidak terdapat data yang hilang sehingga seluruh data dapat digunakan dalam proses analisis SEM-PLS.

---

## Latihan 2 — Anomaly Investigation

Periksa data Anda untuk anomali. Gunakan metode IQR atau z-score.

**Dataset sampel (atau data Anda sendiri):**

| Run | Accuracy (%) |
|-----|-------------|
| 1 | 4,5 |
| 2 | 4,2 |
| 3 | 4,7 |
| 4 | 2,1 |
| 5 | 4,4 |

**Deteksi outlier:**
- Q1 = 4,2 | Q3 = 4,5 | IQR = 0,3
- Batas bawah (Q1 - 1.5×IQR) = 3,75
- Batas atas (Q3 + 1.5×IQR) = 4,95
- Outlier terdeteksi: Responden 4 (2,1)

**Investigasi (untuk setiap outlier):**

| Outlier | Nilai | Kemungkinan Penyebab | Keputusan |
|---------|-------|---------------------|-----------|
| Responden 4 | 2,1 | Tingkat adopsi e-commerce sangat rendah | Tetap dipertahankan karena masih mencerminkan kondisi nyata responden |

---

## Latihan 3 — Validation Report

Buat laporan validasi ringkas untuk dataset eksperimen Anda.

**1. Completeness:** 100% data berhasil terkumpul sesuai target penelitian yaitu 100 pelaku UMKM Mitra Grab Kabupaten Garut.
**2. Format:** [ ☑ ] Konsisten / [ ] Seluruh data menggunakan format yang sama dengan skala Likert 1–5.
**3. Range check (anomali):** 
 Tidak ditemukan nilai di luar rentang yang telah ditentukan.

  Seluruh jawaban responden berada pada rentang 1 sampai 5.

**4. Logic check:** [ ☑ ] Parameter sesuai plan / [ ] Ada ketidaksesuaian: -

**Kesimpulan:** [ ☑ ] Data siap analisis / [ ] Perlu tindakan: 

---

## Refleksi

> Apa perbedaan antara "data yang benar" dan "data yang dipercaya"? Mengapa proses validasi formal diperlukan meskipun data dikumpulkan secara otomatis?

> Data yang benar belum tentu menjadi data yang dipercaya. Data yang benar hanya menunjukkan bahwa nilai yang dicatat sesuai dengan hasil pengukuran. Sebaliknya, data yang dipercaya adalah data yang telah melalui proses validasi, pemeriksaan konsistensi, pengecekan kelengkapan, serta verifikasi logika sehingga dapat dipertanggungjawabkan secara ilmiah.
> Proses validasi formal tetap diperlukan meskipun data dikumpulkan secara otomatis karena kesalahan dapat terjadi pada proses input, penyimpanan, maupun pengolahan data. Dengan validasi yang sistematis, kualitas data dapat dijamin sehingga hasil analisis SEM-PLS menjadi lebih akurat, valid, dan dapat direplikasi oleh peneliti lain.
