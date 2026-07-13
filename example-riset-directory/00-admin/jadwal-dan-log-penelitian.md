# Jadwal & Log Pelaksanaan Penelitian

Catatan kronologis pelaksanaan tiap tahap (sumber: riwayat commit git & dokumen `09-docs/tahap-N-*.md`). Tanggal mengikuti `git log` asli.

## Log Pelaksanaan

| Tanggal | Tahap | Aktivitas | Referensi |
|---|---|---|---|
| 2026-03-31 s.d. 2026-04-06 | Tahap 1 (WS-01 & WS-02) | Pertemuan pertama kuliah; penjelasan tata cara riset kuantitatif replikasi oleh Dosen; penentuan tema integrasi TAM dan RBV pada UMKM mitra Grab di Kabupaten Garut. | [01-proposal/README.md](../01-proposal/README.md) |
| 2026-04-13 s.d. 2026-04-20 | Tahap 1 (WS-03 & WS-04) | Studi literatur mendalam terkait metodologi *Structural Equation Modeling* (SEM-PLS) dan penyusunan proposal penelitian awal. | [02-literatur/README.md](../02-literatur/README.md) |
| 2026-04-27 s.d. 2026-05-11 | Tahap 2 (WS-05 & WS-06) | Penyebaran kuesioner skala Likert 1–5 dan penapisan data lapangan menggunakan skrip otomasi *Data Refinement Pipeline*. | [04-data/raw-kuesioner-umkm.csv](../04-data/raw-kuesioner-umkm.csv) |
| 2026-05-18 s.d. 2026-06-01 | Tahap 3 (WS-07 & WS-08) | Eksekusi prosedur *listwise deletion* untuk menangani *missing values*, menghasilkan dataset bersih berisi **98 responden valid**. | [05-kode/kode.md](../05-kode/kode.md) |
| 2026-06-08 | Tahap 4 (WS-09) | Konfigurasi penguncian algoritma SmartPLS 4.0 dengan parameter 5.000 *subsamples* dan pengaturan *fixed random seed* 42 untuk uji *bootstrapping*. | [05-kode/setup-smartpls.md](../05-kode/setup-smartpls.md) |
| 2026-06-15 s.d. 2026-06-23 (Minggu ke-13) | Tahap 4 & 5 (WS-10 & WS-11) | **Penyelesaian WS-10 & WS-11:** Mengikuti panduan pengerjaan Dosen di kelas; ekspor otomatis matriks evaluasi *Outer Model* (AVE, CR, HTMT) dan *Inner Model* ($R^2$ & Koefisien Jalur); penyusunan draf *manuskrip jurnal*; serta pengisian kelengkapan Laporan Akhir formal. | [00-admin/README.md](README.md), [06-output/](../06-output/) |

## Status Ringkas

*   **Tahap 1–4**: Selesai (dataset bersih final: 98 sampel valid dikunci dengan seed 42, 2026-06-15).
*   **Tahap 5**: Seluruh konten draf naskah artikel ilmiah selesai dikonsolidasi dengan pembuktian signifikansi ketiga hipotesis ($H_1, H_2, H_3$ diterima). Menyisakan keputusan final pengiriman (*submission*) ke target jurnal Sinta 2.

## Item Tindak Lanjut (Checklist Progres Riset)

*   [x] Konfirmasi validitas instrumen pengukuran kuesioner skala Likert 1–5 untuk seluruh indikator variabel.
*   [x] Penyusunan draf proposal penelitian struktural di dalam repositori (`01-proposal/proposal-penelitian.md`).
*   [x] Pemetaan studi literatur empirls terdahulu dan analisis gap riset (`02-literatur/matriks-literatur.md`).
*   [x] Desain diagram arsitektur hubungan kausalitas (*Inner Model Struktural*) dengan diagram Mermaid di `03-teori/arsitektur-dan-skema.md`.
*   [x] Penentuan format bahasa naskah menggunakan Bahasa Indonesia standar akademik untuk laporan Universitas Putra Bangsa.
*   [x] Sinkronisasi dan pembersihan seluruh tautan rusak/lama di dalam *workspace* VS Code.
*   [x] Eksekusi pembersihan data otomatis menggunakan skrip Python (`generate_output_assets.py`) untuk penapisan *missing values*.
*   [x] Validasi kualifikasi pengujian *Outer Model* (Nilai AVE >= 0,50 dan *Composite Reliability* >= 0,70).
*   [x] Pembuktian signifikansi hipotesis linier lewat parameter kritis *T-Statistic* $> 1,96$ dan *P-Value* $< 0,05$.
*   [x] Pemindahan grafik visualisasi performa model (`.png`) serta tabel ringkasan ke dalam dokumen template laporan akhir (`.docx`).

## Korespondensi

*(belum ada — tambahkan catatan korespondensi dengan dosen pembimbing atau editor Jurnal setelah proses submission dimulai)*