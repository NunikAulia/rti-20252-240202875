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
  Missing: 0 dari 5 data points

Format Consistency:
  [ ☑ ] Semua file format sama (CSV/JSON/...)
  [ ☑ ] Header konsisten
  [ ☑ ] Tipe data konsisten (numerik tetap numerik)

Range & Logic:
  [ ☑ ] Nilai dalam range masuk akal
  [ ☑ ] Tidak ada waktu negatif
  [ ☑ ] Metrik 0–100%, tidak di luar range
  Anomali ditemukan: Tidak ditemukan anomali yang signifikan. Seluruh nilai validitas, reliabilitas, dan pengujian hipotesis berada dalam batas yang dapat diterima.

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
| SEM-PLS UMKM Grab | 5 | 5 | 0 | - |

**Total expected:** 5 | **Total actual:** 5 | **Missing:** 0

**Keputusan untuk data missing:**
> Tidak terdapat data yang hilang sehingga seluruh data dapat digunakan untuk proses analisis statistik.

---

## Latihan 2 — Anomaly Investigation

Periksa data Anda untuk anomali. Gunakan metode IQR atau z-score.

**Dataset sampel (atau data Anda sendiri):**

| Run | Accuracy (%) |
|-----|-------------|
| 1 | 0,880 |
| 2 | 0,881 |
| 3 | 0,879 |
| 4 | 0,882 |
| 5 | 0,878 |

**Deteksi outlier:**
- Q1 = 0,879 | Q3 = 0,881 | IQR = 0,002
- Batas bawah (Q1 - 1.5×IQR) = 0,876
- Batas atas (Q3 + 1.5×IQR) = 0,884
- Outlier terdeteksi: Tidak Ada

**Investigasi (untuk setiap outlier):**

| Outlier | Nilai | Kemungkinan Penyebab | Keputusan |
|---------|-------|---------------------|-----------|
| Tidak Ada | - | - | Data dipertahankan |

---

## Latihan 3 — Validation Report

Buat laporan validasi ringkas untuk dataset eksperimen Anda.

**1. Completeness:** 100% data terkumpul
**2. Format:** [ ☑ ] Konsisten / [ ] Ada inkonsistensi: Semua data menggunakan format yang sama dan dapat dibaca oleh SmartPLS tanpa error.
**3. Range check (anomali):** 
  Nilai Outer Loading berada di atas 0,70.
  Nilai AVE berada di atas 0,50.
  Nilai Composite Reliability berada di atas 0,70.
  Nilai R-Square sebesar 0,880.
  Nilai P-Value seluruh hipotesis sebesar 0,000.

Tidak ditemukan nilai yang berada di luar batas logis penelitian.
**4. Logic check:** [ ☑ ] Parameter sesuai plan / [ ] Ada ketidaksesuaian: =

**Kesimpulan:** [ ☑ ] Data siap analisis / [ ] Perlu tindakan: Seluruh data telah memenuhi aspek completeness, consistency, validity, dan accuracy sehingga layak digunakan untuk analisis dan penarikan kesimpulan penelitian.

---

## Refleksi

> Apa perbedaan antara "data yang benar" dan "data yang dipercaya"? Mengapa proses validasi formal diperlukan meskipun data dikumpulkan secara otomatis?

> Data yang benar belum tentu merupakan data yang dipercaya. Data yang benar hanya menunjukkan bahwa data berhasil tercatat, sedangkan data yang dipercaya adalah data yang telah melalui proses validasi sehingga kualitasnya dapat dipertanggungjawabkan secara ilmiah.
> Proses validasi formal tetap diperlukan meskipun data dikumpulkan secara otomatis karena kesalahan dapat terjadi pada sistem pencatatan, proses input, format data, maupun konfigurasi perangkat lunak. Tanpa validasi, peneliti berisiko menggunakan data yang tidak lengkap, tidak konsisten, atau mengandung anomali yang dapat memengaruhi hasil penelitian.
> Melalui proses validasi, peneliti dapat memastikan bahwa data yang digunakan benar-benar sesuai dengan rancangan eksperimen dan layak digunakan sebagai dasar pengambilan kesimpulan ilmiah.
