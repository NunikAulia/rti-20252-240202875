# 06-output

Hasil olahan data statistik inferensial & visualisasi model — **Tahap 4 (Evaluasi Model SEM-PLS)**.

Dihasilkan secara otomatis berdasarkan konfigurasi parameter perangkat lunak SmartPLS 4.0 (Complete Bootstrapping, 5.000 *subsamples*, *fixed seed* 42) menggunakan skrip otomatisasi `generate_output_assets.py` terhadap dataset bersih 98 responden valid.

## tables/

| File | Isi |
|---|---|
| `descriptive_stats.csv` | Nilai statistik deskriptif item indikator kuesioner ($X_{1\_1}$ s.d $Y_4$) mencakup nilai *Mean*, *Standard Deviation*, *Minimum*, dan *Maximum* dari 98 responden valid[cite: 2]. |
| `construct_reliability_validity.csv` | Matriks evaluasi konsistensi internal tingkat tinggi dan validitas konvergen, memuat nilai *Cronbach's Alpha*, *Composite Reliability* (CR), dan *Average Variance Extracted* (AVE) untuk tiap konstruk laten[cite: 2]. |
| `path_coefficients.csv` | Ringkasan hasil parameter pengujian hipotesis struktural kausalitas, meliputi nilai *Path Coefficient* ($\beta$), nilai *T-Statistic* hasil *bootstrapping*, *P-Value*, serta status konfirmasi keputusan statistik[cite: 2]. |

## figures/

| File | Isi |
|---|---|
| `fig_path_coefficients.png` | Bar chart visualisasi kekuatan dan perbandingan kontribusi Koefisien Jalur Struktural (*Path Coefficient*) antar-variabel laten independen ($X_1, X_2, X_3$) terhadap peningkatan omzet ($Y$)[cite: 2]. |
| `fig_hypothesis_t_statistics.png` | Bar chart uji signifikansi nilai *T-Statistic* hasil prosedur *bootstrapping* yang dilengkapi dengan garis ambang batas kritis signifikansi dua arah pada nilai $\text{T} = 1,96$[cite: 2]. |

## Acuan

- Log Pembersihan Data Lapangan & Analisis *Missing Values*: [../04-data/README.md](../04-data/README.md)
- Protokol Penguncian Parameter Konfigurasi Perangkat Lunak: [../05-kode/setup-smartpls.md](../05-kode/setup-smartpls.md)