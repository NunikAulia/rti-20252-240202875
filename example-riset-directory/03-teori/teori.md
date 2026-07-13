# 03-teori

Kerangka konseptual, hipotesis, dan landasan teori struktural sistem hubungan kausalitas — hasil dari **Tahap 1 (Konseptualisasi Model)**.

## Isi yang diharapkan

- Diagram Alur Iterasi Model (Tahapan Rekayasa SEM-PLS)
- Spesifikasi Persamaan Struktural Laten (Integrasi Kerangka Konseptual TAM dan RBV)
- Operasionalisasi Matriks Variabel Kontrol dan Laten ($X_1, X_2, X_3$, dan $Y$)
- Diagram Arsitektur Hubungan Kausalitas (Struktural Inner Model)

## Berkas

- [arsitektur-dan-skema.md](arsitektur-dan-skema.md) — Diagram Mermaid yang memetakan Alur Desain Riset, Skema Hubungan Laten (Path Model Diagram), dan Spesifikasi Hubungan Refleksif antar-indikator.

## Acuan

- Formulasi Teoretis Awal: Landasan State of the Art dan Identifikasi Research Gap di [../01-proposal/README.md](../01-proposal/README.md)
- Deskripsi Operasional Item Kuesioner: Definisi Instrumen Pengukuran Final di [../05-kode/kuesioner-final.md](../05-kode/kuesioner-final.md)

---

## Landasan Teoretis Integratif

Model riset ini dibangun dengan mensinergikan dua landasan teoretis utama sistem manajemen informasi:
1. **Technology Acceptance Model (TAM):** Digunakan sebagai basis konstruk *Manfaat yang Dirasakan* ($X_1$) untuk mengukur keyakinan fungsional pelaku usaha terhadap platform digital.
2. **Resource-Based View (RBV):** Digunakan sebagai basis konstruk *Kapabilitas Teknologi* ($X_2$) dan *Tingkat Adopsi E-Commerce* ($X_3$) untuk mengukur sejauh mana aset digital internal bertindak sebagai kapabilitas unik untuk mengeksploitasi peluang pasar, yang bermuara pada *Peningkatan Omzet UMKM* ($Y$).

## Formulasi Persamaan Struktural Model

Secara matematis, pengujian *Inner Model* dalam penelitian kuantitatif ini dirumuskan ke dalam persamaan struktural kausalitas linier sebagai berikut:

$$Y = \beta_1 X_1 + \beta_2 X_2 + \beta_3 X_3 + \zeta$$

Di mana:
*   $Y$ = Peningkatan Omzet UMKM
*   $X_1$ = Manfaat yang Dirasakan (*Perceived Benefits*)
*   $X_2$ = Kapabilitas Teknologi (*Technology Capability*)[cite: 2]
*   $X_3$ = Tingkat Adopsi *E-Commerce* (*E-Commerce Adoption*)[cite: 2]
*   $\beta_1, \beta_2, \beta_3$ = Koefisien Jalur Struktural (*Path Coefficients*)[cite: 2]
*   $\zeta$ = *Residual Error* (Variansi yang tidak terjelaskan oleh model struktural)[cite: 2]