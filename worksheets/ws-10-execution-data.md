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
| 1	| Analisis SEM-PLS Dataset UMKM	| 42	| Bootstrap=5000 |	Planned| 	30 menit	| output_run1.xlsx |
| 2	| Analisis SEM-PLS Dataset UMKM	| 123	| Bootstrap=5000	| Planned	| 30 menit	| output_run2.xlsx |
| 3	| Analisis SEM-PLS Dataset UMKM	| 456	| Bootstrap=5000 |	Planned	| 30 menit	| output_run3.xlsx | 
| 4	| Analisis SEM-PLS Dataset UMKM	| 789	| Bootstrap=5000	| Planned	| 30 menit	| output_run4.xlsx |
| 5	| Analisis SEM-PLS Dataset UMKM	| 999	| Bootstrap=5000 | Planned	| 30 menit | output_run5.xlsx |      

Jumlah runs per skenario : 5
Total runs               : 5

DATA LOG (per run):
  Run ID    : run-001
  Timestamp : 2025-06-15 09:00:00
  Skenario  : Analisis Pengaruh E-Commerce terhadap Peningkatan Omzet UMKM
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
| 1	SEM-PLS UMKM Grab	| 42	| Bootstrap=5000	| Planned |
| 2	SEM-PLS UMKM Grab	| 123	| Bootstrap=5000	| Planned |
| 3	SEM-PLS UMKM Grab	| 456	| Bootstrap=5000	| Planned |
| 4	SEM-PLS UMKM Grab	| 789	| Bootstrap=5000	| Planned |
| 5	SEM-PLS UMKM Grab	| 999	| Bootstrap=5000	| Planned |

**Total skenario:** 1
**Run per skenario:** 5
**Total run keseluruhan:** 5

---

## Latihan 2 — Data Log Terstruktur

Desain format data log untuk eksperimen Anda. Tentukan field apa saja yang akan dicatat.

**Identitas:**
| Field | Contoh |
|-------|--------|
| Run ID	| run-001 |
| Timestamp	| 2025-06-15T09:00:00 |
| Skenario	| SEM-PLS UMKM Grab |
| Peneliti	| Nunik Aulia Primadani |
| Dataset	| UMKM_Grab_100Responden.xlsx |

**Konfigurasi:**
| Field | Contoh |
|-------|--------|
| Seed	| 42 |
| Code Version	| SmartPLS v4.0 |
| Bootstrap	| 5000 |
| Significance Level	| 0,05 |
| Sample Size	| 100 |

**Hasil:**
| Metrik | Tipe Data | Range Valid |
|--------|----------|-------------|
| Outer Loading	| Float	| 0 – 1 |
| Composite Reliability	| Float	| 0 – 1 |
| AVE	| Float	| 0 – 1 |
| Cronbach Alpha	| Float	| 0 – 1 |
| R-Square	| Float	| 0 – 1 |
| F-Square	| Float	| ≥ 0 |
| P-Value	| Float	| 0 – 1 |
| T-Statistic	| Float	| ≥ 0 |

**Format output:** [ ☑ ] CSV / [ ] JSON / [ ] Database / [ ] Lainnya: Excel (.xlsx)

---

## Latihan 3 — Anomaly Protocol

Rencanakan bagaimana menangani anomali. Untuk setiap jenis, tentukan langkah yang diambil.

| Jenis Anomali | Contoh | Tindakan |
|---------------|--------|----------|
| Run gagal (crash)	| SmartPLS berhenti saat bootstrapping	| Dokumentasikan error, restart aplikasi, jalankan ulang, catat perubahan |
| Hasil ekstrem	| Nilai loading factor < 0,70	| Investigasi indikator, evaluasi item, dokumentasikan alasan eliminasi |
| Waktu eksekusi anomali	| Proses jauh lebih lama dari biasanya |	Periksa penggunaan CPU/RAM, ulangi run dan catat hasil | 
| Inkonsistensi dengan run lain	| Nilai R-Square berbeda jauh | Verifikasi dataset, seed, dan konfigurasi analisis |

**Prinsip:** Detect → Investigate → Document → Decide

---

## Refleksi

> Pernahkah Anda melaporkan hasil riset/tugas dari single run? Apa risikonya? Bagaimana multiple run mengubah kepercayaan terhadap hasil?

**Pengalaman sebelumnya:**
> Pada beberapa tugas penelitian dan praktikum sebelumnya, hasil sering dilaporkan berdasarkan satu kali proses analisis saja (single run). Risiko dari pendekatan tersebut adalah hasil yang diperoleh bisa dipengaruhi oleh kondisi tertentu, kesalahan konfigurasi, atau faktor acak sehingga kurang mewakili kondisi sebenarnya.
**Yang akan dilakukan berbeda:**
> Pada penelitian ini, analisis akan dilakukan dengan beberapa run menggunakan seed yang berbeda serta seluruh konfigurasi dan hasil dicatat dalam data log. Dengan demikian, hasil penelitian menjadi lebih konsisten, dapat diverifikasi, dan memiliki tingkat kepercayaan yang lebih tinggi.
