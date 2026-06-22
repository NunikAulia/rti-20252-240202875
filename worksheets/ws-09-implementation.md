# WS-09: Implementation & Environment

> **Bab 9 — Implementasi Riset & Kontrol Lingkungan**

---

## Ringkasan Materi

### Implementasi Riset ≠ Coding Biasa

Tujuan implementasi riset bukan membuat software yang berfungsi, melainkan membangun **instrumen pengukuran yang konsisten**. Setiap modul harus di-mapping ke variabel (dari Bab 6), parameter harus config-driven, dan logging aktif dari hari pertama.

> **Mengapa reproducibility penting?** Sains dibangun di atas prinsip verifikasi — temuan harus bisa dikonfirmasi oleh peneliti lain. _Replicability crisis_ yang terjadi di banyak paper riset ML/AI disebabkan oleh environment tidak terdokumentasi: orang lain tidak bisa reproduksi, hasil diragukan, kepercayaan terhadap temuan hilang. Prinsip: **dokumentasi environment = snapshot kredibilitas riset Anda.**

### Reproducible Implementation Model

```
Design → Implementation → Environment Setup → Execution Consistency → Reproducibility → Trustworthy Result
```

Setiap transisi memiliki syarat:
- Design → Implementation: kode sesuai mapping variabel-ke-komponen
- Implementation → Environment: versi, dependency, seed, path, OS eksplisit
- Environment → Consistency: seed terkunci, urutan deterministik
- Consistency → Reproducibility: dokumentasi lengkap
- Reproducibility → Trust: siapa pun ikuti dokumentasi → hasil sama/serupa

### Repeatability vs Reproducibility

| Level | Peneliti | Environment | Hasil |
|-------|---------|-------------|-------|
| **Repeatability** | Sama | Sama | Sama persis |
| **Reproducibility** | Berbeda | Berbeda (ikuti docs) | Sama/serupa |

Capai **repeatability** dulu, baru **reproducibility**.

### Engineering vs Research Perspective

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Sistem berfungsi untuk user | Instrumen pengukuran konsisten |
| Dependency | Update ke terbaru | Lock di versi spesifik |
| Testing | Unit, integration, E2E | Repeatability test (run ulang → sama?) |
| Dokumentasi | User guide, API docs | Environment spec, execution steps, expected output |
| Config | Default masuk akal | Setiap parameter eksplisit & adjustable |

### Jebakan Kognitif

1. Menunda environment setup → bug sulit dilacak
2. Tidak pakai version control → hasil tidak bisa direkonstruksi
3. Menolak Docker/container → "di laptop saya bisa" saat review
   - **Docker** = teknologi container yang "membungkus" aplikasi beserta seluruh dependency-nya dalam satu unit terisolasi. Hasilnya: kode berjalan identik di laptop, server, maupun reviewer lain. Intro singkat: `docker run -v $(pwd):/workspace environment-image python run_experiment.py`
4. 3× hasil sama ≠ repeatable (bisa cache/state tersimpan)

### Dependency Locking

Mengandalkan "install library terbaru" berbahaya: versi berbeda = perilaku berbeda = hasil tidak reproducible. Praktik:
- **Python**: buat `requirements.txt` dengan versi eksplisit: `scikit-learn==1.3.2`, lalu kunci dengan `pip freeze > requirements.txt`
- **Conda**: gunakan `conda env export > environment.yml` untuk snapshot lengkap
- **Node.js/R/Julia**: gunakan `package-lock.json` / `renv.lock` / `Project.toml` — semua fungsi serupa: lock versi + hash

### Istilah Penting

- **Environment Specification** — Deskripsi lengkap: hardware, OS, runtime, library + versi, config, seed
- **Dependency** — Komponen eksternal yang harus di-lock versinya
- **Config-driven** — Parameter dieksternalisasi ke file konfigurasi, bukan hardcode

---

## Template A.9 — Dokumentasi Setup Eksperimen

```
EXPERIMENT SETUP DOCUMENTATION

Hardware:
  CPU     : Intel Core i5-1135G7
  RAM     : 8 GB DDR4
  GPU     : Intel Iris Xe Graphics
  Storage : SSD 512 GB

Software:
  OS        : Windows 11 Pro 64-bit
  Runtime   : Java Runtime Environment (JRE) 17
  Framework : SmartPLS 4

Dependencies:
| Library | Version | Sumber | Hash/Checksum |
|---------|---------|--------|---------------|
|     SmartPLS	| 4.0	| SmartPLS Official	| N/A |
| Microsoft Excel | 2021	| Microsoft	| N/A |
| IBM SPSS Statistics	| 26	| IBM	| N/A |
| Java Runtime Environment	| 17	| Oracle	| N/A |
| Windows 11	| 23H2	| Microsoft	| N/A    | 

Konfigurasi:
  Config file     : Dataset_Kuesioner_UMKM.xlsx
  Random seed     : 42
  Hyperparameters : 
  - Minimum loading factor > 0,70
  - Composite Reliability > 0,70
  - AVE > 0,50
  - Bootstrapping = 5000 subsamples
  - Signifikansi α = 0,05

Reproducibility Check:
  [ ☑ ] Dependency terdokumentasi (requirements.txt / lock file)
  [ ☑ ] Seed ditetapkan di semua level (Python, NumPy, framework)
  [ ☑ ] Config di version control
  [ ☑ ] README instruksi reproduksi lengkap
```

---

## Latihan 1 — Environment Specification

Dokumentasikan environment untuk eksperimen Anda (boleh environment saat ini atau yang direncanakan).

| Komponen | Spesifikasi |
|----------|------------|
| CPU | Intel Core i5-1135G7, 4 Core 8 Thread |
| RAM | 8 GB DDR4 |
| GPU | Intel Iris Xe Graphics |
| OS | Windows 11 Pro 64-bit |
| Runtime | Java Runtime Environment (JRE) 17 |
| Framework | SmartPLS 4 |
| Random Seed | 42 |

**Dependencies (minimal 5):**

| Library | Version | Alasan Dibutuhkan |
|---------|---------|-------------------|
| SmartPLS	| 4.0	| Analisis SEM-PLS |
| Microsoft Excel	| 2021	| Input dan pembersihan data |
| IBM SPSS	| 26	| Uji instrumen awal |
| Java Runtime	| 17	| Menjalankan SmartPLS |
| Windows 11 SDK	| 23H2	| Dukungan sistem operasi |

---

## Latihan 2 — Repeatability Test Plan

Rancang tes repeatability sederhana: jalankan kode yang sama 3× di environment yang sama.

| Run | Seed | Metrik Utama | Hasil Sama? |
|-----|------|-------------|-------------|
| 1 | 42 | R-Square = 0,880 | — |
| 2 | 42 | R-Square = 0,880 | [ ☑ ] Ya / [ ] Tidak |
| 3 | 42 | R-Square = 0,880 | [ ☑ ] Ya / [ ] Tidak |

**Jika hasil berbeda, kemungkinan penyebab:**

> Penyebab umum non-repeatability:
> - **Thermal throttling** — CPU/GPU overheating pada run berturut-turut → clock speed turun → waktu eksekusi berubah
> - **Background process** — antivirus scan, update OS, atau cloud sync aktif saat run berlangsung
> - **Cache dari run sebelumnya** — hasil tersimpan di memori/disk sehingga run berikutnya tidak menjalankan komputasi penuh
> - **Random state tidak dikontrol di semua level** — Python seed di-set, tapi NumPy/PyTorch/TensorFlow punya seed independen

___________________________________________________

**Checklist kontrol yang sudah diterapkan:**
- [ ☑ ] Random seed di-set di semua level
- [ ☑ ] Tidak ada background process yang mengganggu
- [ ☑ ] Cache dibersihkan antar-run
- [ ☑ ] Config file yang sama untuk semua run

---

## Latihan 3 — README Eksperimen

Tulis README minimum untuk eksperimen Anda (6 komponen wajib).

```
# Judul Eksperimen: Pengaruh E-Commerce terhadap Peningkatan Omzet UMKM Bermitra Grab di Kabupaten Garut

## 1. Environment
> Hardware:

Intel Core i5-1135G7
RAM 8 GB
SSD 512 GB

  Software:

Windows 11 Pro
SmartPLS 4
Microsoft Excel 2021
IBM SPSS 26

## 2. Installation
> Install Java Runtime Environment 17
  Install SmartPLS 4
  Install Microsoft Excel 2021
  Install IBM SPSS Statistics 26
  Pastikan seluruh software berjalan normal

## 3. Data
> Sumber data:
  - Kuesioner pelaku UMKM mitra Grab

  Jumlah responden:
  - 100 responden

  Format data:
  - Microsoft Excel (.xlsx)

  Variabel:
  - E-Commerce (X)
  - Manfaat yang Dirasakan
  - Kapabilitas Teknologi
  - Tingkat Adopsi
  - Peningkatan Omzet (Y)
  - Peningkatan Hasil
  - Kecukupan Hasil
  - Dapat Berkembang

## 4. Execution
> Import dataset ke SmartPLS
  Bentuk model penelitian
  Jalankan PLS Algorithm
  Jalankan Bootstrapping
  Analisis Outer Model
  Analisis Inner Model
  Interpretasi hasil

## 5. Configuration
> Random Seed = 42
  Bootstrapping = 5000
  Significance Level = 0,05
  Loading Factor Minimum = 0,70
  Composite Reliability Minimum = 0,70
  AVE Minimum = 0,50

## 6. Expected Output
> Output yang diharapkan:

Nilai Outer Loading > 0,70
Composite Reliability > 0,70
AVE > 0,50
R-Square = 0,880
P-Value < 0,05
Hipotesis diterima

  Output akhir berupa:

Tabel Validitas
Tabel Reliabilitas
Tabel R-Square
Tabel F-Square
Tabel Uji Hipotesis
Kesimpulan penelitian

```

---

## Refleksi

> Apakah eksperimen Anda saat ini bisa direproduksi oleh orang lain tanpa bantuan Anda? Komponen apa yang masih hilang? Ya, Karena spesifikasi perangkat, software, data, langkah analisis, parameter, dan output yang diharapkan telah didokumentasikan.

**Level saat ini:** [ ] Repeatability / [ ☑ ] Reproducibility / [ ] Belum keduanya
**Komponen yang belum terdokumentasi:**
> Backup dataset mentah
  Dokumentasi perubahan data (data cleaning log)
  Screenshot konfigurasi SmartPLS
  Repository penyimpanan file penelitian
