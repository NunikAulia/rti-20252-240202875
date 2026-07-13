# Protokol Pengaturan Perangkat Lunak SmartPLS (setup-smartpls.md)

Dokumen acuan konfigurasi parameter algoritma pada software SmartPLS 4.0 untuk menjamin replikasi (*repeatability*) pengujian statistik inferensial model.

---

## 1. Spesifikasi Model Pengukuran (Outer Model)

* **Jenis Model:** Refleksif (seluruh indikator merefleksikan konstruk latennya).
* **Skema Pembobotan (*Weighting Scheme*):** Path Weighting Scheme.
* **Kriteria Berhenti (*Stop Criterion*):** $1 \times 10^{-7}$
* **Maksimum Iterasi:** 300 iterasi.

---

## 2. Pengaturan Parameter Analisis Inferensial (Inner Model)

Evaluasi signifikansi koefisien jalur dilakukan melalui prosedur *Complete Bootstrapping* dengan aturan ketat berikut:

| Parameter SmartPLS 4.0 | Konfigurasi Pengaturan | Justifikasi Akademik |
| :--- | :--- | :--- |
| **Subsamples** | 5.000 *subsamples* | Standar baku Hair et al. (2021) untuk mendapatkan estimasi parameter yang stabil. |
| **Bootstrapping Type** | Complete Bootstrapping | Menghasilkan parameter pengujian parameter lanjutan yang lebih komprehensif. |
| **Random Seed** | Fixed Seed: 42 | Menjamin hasil pengujian nilai statistik tetap konsisten saat direplikasi ulang (*reproducibility*). |
| **Significance Level** | 0.05 ($\alpha = 5\%$) | Batas toleransi standard dalam riset manajemen perilaku bisnis kuantitatif. |
| **Test Type** | Two-Tailed (Dua Arah) | Digunakan karena arah pengujian hipotesis adalah pengujian pengaruh umum secara signifikan. |

---

## 3. Ambang Batas Evaluasi Keputusan Statistik

### A. Uji Validitas & Reliabilitas (Outer Model)
* **Outer Loading Indikator:** $\ge 0,70$
* **Average Variance Extracted (AVE):** $\ge 0,50$
* **Composite Reliability (CR) & Cronbach's Alpha:** $\ge 0,70$
* **Rasio HTMT (Validitas Diskriminan):** $< 0,85$

### B. Uji Struktural & Hipotesis (Inner Model)
* **T-Statistic Hitung:** $> 1,96$
* **P-Value:** $< 0,05$
* **Ukuran Efek ($f^2$):** 
  * `0,02` (kecil)
  * `0,15` (sedang)
  * `0,35` (besar)