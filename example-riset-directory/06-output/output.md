# 06-output

Hasil olahan data statistik inferensial & visualisasi model — **Tahap 4 (Evaluasi Model SEM-PLS)**.

Dihasilkan secara otomatis berdasarkan konfigurasi lingkungan *software* SmartPLS 4.0 (Complete Bootstrapping, 5.000 *subsamples*, *fixed seed* 42) dari dataset bersih `clean_data_smartpls.csv` (98 data responden valid pasca-*listwise deletion*).

## tables/

| Nama Berkas | Isi / Deskripsi Matriks Statistik |
| :--- | :--- |
| `descriptive_stats.csv` | Statistik deskriptif data awal indikator kuesioner ($X_1$, $X_2$, $X_3$, $Y$) mencakup nilai *Mean*, *Standard Deviation*, *Minimum*, dan *Maximum* dari 98 responden bersih. |
| `outer_model_loading.csv` | Nilai *Outer Loading* untuk memastikan validitas konvergen tiap butir pertanyaan ($\ge 0,70$). |
| `construct_reliability_validity.csv` | Evaluasi reliabilitas konstruk dan validitas konvergen tingkat tinggi: *Cronbach's Alpha*, *Composite Reliability* (CR), dan *Average Variance Extracted* (AVE). |
| `discriminant_validity_htmt.csv` | Matriks rasio *Heterotrait-Monotrait Ratio* (HTMT) untuk memverifikasi validitas diskriminan antar-konstruk laten ($< 0,85$). |
| `path_coefficients.csv` | Parameter koefisien jalur struktural, nilai *T-Statistic*, dan *P-Value* dari pengujian hipotesis H$_1$, H$_2$, dan H$_3$. |
| `model_fit_r_square.csv` | Kriteria kekuatan prediksi model berupa nilai Koefisien Determinasi ($R^2$) dan Kriteria Ukuran Efek ($f^2$) untuk masing-masing jalur. |

## figures/

| Nama Berkas | Isi / Deskripsi Visualisasi Grafik |
| :--- | :--- |
| `fig_outer_loadings.png` | Bar chart nilai *Outer Loading* untuk setiap indikator variabel terhadap konstruk latennya masing-masing. |
| `fig_path_coefficients.png` | Bar chart visualisasi kekuatan pengaruh Koefisien Jalur Struktural (*Path Coefficient*) antar-variabel laten. |
| `fig_hypothesis_t_statistics.png` | Diagram perbandingan nilai *T-Statistic* hasil *bootstrapping* terhadap ambang batas signifikansi kualifikasi 1,96. |
| `fig_r_square_contribution.png` | Pie chart kontribusi variansi independen ($X_1$, $X_2$, $X_3$) dalam menjelaskan variabel dependen Peningkatan Omzet ($Y$). |
| `fig_sem_pls_model_structure.png` | Diagram arsitektur struktural utuh model hubungan kausalitas (Manfaat, Kapabilitas, Adopsi $\rightarrow$ Omzet). |

## Acuan

- Dataset Bersih dan Log Validasi Lapangan: [../04-data/README.md](../04-data/README.md)
- Spesifikasi Pengaturan Bootstrapping: Protokol Parameter Perangkat Lunak di [../05-kode/setup-smartpls.md](../05-kode/setup-smartpls.md)