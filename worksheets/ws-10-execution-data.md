# WS-10: Experiment Execution & Data Collection

> **Bab 10 — Eksekusi Eksperimen & Pengumpulan Data**

---

## Ringkasan Materi

### Experiment Execution Pipeline

```
Design → Execution Plan → Controlled Execution → Data Collection → Data Logging → Dataset for Analysis
```

### Multiple Run = Non-Negotiable

Single run **tidak pernah cukup** untuk klaim ilmiah. Minimum 5-10 run per skenario dengan seed berbeda. Multiple run menghasilkan:
- Mean, std, confidence interval
- Distribusi hasil → uji statistik
- Variabilitas → error bar di grafik

### Execution Plan

Setiap eksperimen harus memiliki plan sebelum eksekusi:
- Daftar skenario
- Jumlah run per skenario
- Random seed per run (pre-determined!)
- Urutan eksekusi (randomisasi/counterbalancing)
- Pre-execution checklist

### Data Logging Komprehensif

Setiap run menghasilkan log terstruktur:
1. **Identitas** — Run ID, timestamp, skenario
2. **Konfigurasi** — Semua parameter, seed, code version
3. **Hasil** — Semua metrik, output detail
4. **Metadata** — Waktu eksekusi, resource usage, warning/error

Format: CSV/JSON/database — **bukan stdout yang di-copy-paste**.

### Engineering vs Research Execution

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Run | Sekali (deploy) | Multiple (min 5-10, seed berbeda) |
| Logging | Error log, access log | Semua parameter, metrik, metadata |
| Anomali | Bug → fix → redeploy | Investigasi → dokumentasi → analisis |
| Urutan | Tidak penting | Bisa bias — perlu randomisasi |

### Anomali = Dokumentasi, Bukan Hapus

Run gagal/anomali tidak boleh dihapus tanpa dokumentasi. Bisa jadi:
- **Bug** → fix & re-run (dokumentasikan!)
- **Batas kemampuan metode** → DNF = temuan
- **Data yang bias** jika hanya simpan run "berhasil"

### Jebakan Kognitif

1. "Satu angka cukup" → tanpa distribusi, tidak bisa diuji
2. "Seed tidak penting" → bahkan algoritma deterministik bisa dipengaruhi library stokastik
3. "Run gagal langsung hapus" → kehilangan temuan potensial
4. "Semua run harus hari ini" → thermal throttling, fatigue

---

## Template A.10 — Execution Plan & Data Log

```
EXECUTION PLAN

| Run # | Skenario | Seed | Parameter | Status | Waktu | Output File |
|-------|----------|------|-----------|--------|-------|-------------|
| 1	| Uji Instrumen Awal	| 42	| 100 responden	| Planned	| Minggu 5	| data_raw.xlsx |
| 2	| Outer Model	| 42	| Loading Factor	| Planned	| Minggu 6	| outer_model.xlsx |
| 3	| Reliability Test	| 42	| CR, AVE, Alpha	| Planned	| Minggu 6	| reliability.xlsx |
| 4	| Inner Model	| 42	| Path Coefficient	| Planned	| Minggu 7	| inner_model.xlsx | 
| 5	| Bootstrapping	| 42	| 5000 subsamples	| Planned	| Minggu 7	| bootstrap.xlsx |      

Jumlah runs per skenario : 1
Total runs               : 5

DATA LOG (per run):
  Run ID    : run-001
  Timestamp : 2026-06-20 10:00 WIB
  Skenario  : Pengumpulan Data Kuesioner
  Input     : Dataset hasil kuesioner 100 responden
  Output    : Nilai Outer Loading, AVE, Composite Reliability, R-Square, F-Square, dan Uji Hipotesis
  Anomali   : Tidak ada
  Catatan   : Run berhasil diselesaikan
```

---

## Latihan 1 — Execution Plan

Susun execution plan untuk eksperimen Anda. Tentukan skenario, jumlah run, dan seed sebelum eksekusi.

| Run # | Skenario | Seed | Parameter Kunci | Status |
|-------|----------|------|----------------|--------|
| Pengumpulan Data	| 42	| 100 responden	| Planned |
| Uji Validitas| 42	| Loading Factor > 0,70	| Planned |
| Uji Reliabilitas	| 42	| CR > 0,70 ; AVE > 0,50	| Planned |
| Uji Inner Model	| 42	| R² dan Path Coefficient	| Planned |
| Bootstrapping | 42	| 5000 Subsamples	| Planned |

**Total skenario:** 5
**Run per skenario:** 1
**Total run keseluruhan:** 5

---

## Latihan 2 — Data Log Terstruktur

Desain format data log untuk eksperimen Anda. Tentukan field apa saja yang akan dicatat.

**Identitas:**
| Field | Contoh |
|-------|--------|
| Run ID	| run-001 |
| Timestamp	| 2026-06-20T10:00:00 |
| Nama Penelitian | E-Commerce dan Omzet UMKM |
| Skenario	| Pengumpulan Data |
| Peneliti	| Nunik Aulia Primadani |

**Konfigurasi:**
| Field | Contoh |
|-------|--------|
| Seed	| 42 |
| Software	| SmartPLS v4.0 |
| Sampel	| 100 UMKM |
| Skala	| Likert 1–5 |
| Bootstrap	| 5000 |

**Hasil:**
| Metrik | Tipe Data | Range Valid |
|--------|----------|-------------|
| Outer Loading	| Float	| 0 – 1 |
| Composite Reliability	| Float	| 0 – 1 |
| AVE	| Float	| 0 – 1 |
| Cronbach Alpha	| Float	| 0 – 1 |
| R-Square	| Float	| 0 – 1 |
| Path Coefficient | Float | -1 sampai 1 |
| F-Square	| Float	| ≥ 0 |
| P-Value	| Float	| < 0,05|
| T-Statistic	| Float	| > 1,96 |

**Format output:** [ ☑ ] CSV / [ ] JSON / [ ] Database / [ ] Lainnya: Excel

---

## Latihan 3 — Anomaly Protocol

Rencanakan bagaimana menangani anomali. Untuk setiap jenis, tentukan langkah yang diambil.

| Jenis Anomali | Contoh | Tindakan |
|---------------|--------|----------|
| Run gagal (crash)	| SmartPLS error saat bootstrapping	| Dokumentasi, restart software, jalankan ulang |
| Hasil ekstrem	| Loading Factor < 0,50	| Evaluasi indikator dan hapus indikator tidak valid |
| Waktu eksekusi anomali	| Analisis sangat lambat |	Periksa spesifikasi perangkat dan dataset | 
| Inkonsistensi dengan run lain	| Nilai path coefficient berubah signifikan | Periksa data input dan konfigurasi |

**Prinsip:** Detect → Investigate → Document → Decide

---

## Refleksi

> Pernahkah Anda melaporkan hasil riset/tugas dari single run? Apa risikonya? Bagaimana multiple run mengubah kepercayaan terhadap hasil?

**Pengalaman sebelumnya:**
> Pada penelitian sebelumnya sering kali analisis dilakukan hanya satu kali sehingga hasil yang diperoleh belum tentu konsisten apabila dilakukan pengujian ulang. Risiko dari single run adalah kemungkinan terdapat kesalahan input data, konfigurasi software, atau bias analisis yang tidak terdeteksi.
> Melalui dokumentasi execution plan dan data log yang lengkap, penelitian ini menjadi lebih transparan dan dapat direplikasi oleh peneliti lain. Penggunaan prosedur yang sama pada seluruh responden serta konfigurasi SmartPLS yang konsisten akan meningkatkan kepercayaan terhadap hasil penelitian.

**Yang akan dilakukan berbeda:**
> Analisis dilakukan satu kali tanpa dokumentasi detail mengenai konfigurasi dan proses pengolahan data.

> Yang Akan Dilakukan Berbeda:

> Seluruh proses pengumpulan data, pengolahan data, pengujian validitas, reliabilitas, outer model, inner model, dan bootstrapping akan didokumentasikan secara sistematis sehingga hasil penelitian lebih valid dan dapat direproduksi.
