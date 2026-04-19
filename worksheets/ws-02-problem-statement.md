# WS-02: Problem Statement

> **Bab 2 — Problem Formulation & System Context**

---

## Ringkasan Materi

### Problem Formation Model

Masalah riset melewati 5 tahap transformasi. Melompat langsung dari Reality ke Variable adalah kesalahan paling umum.

```
Reality → Observed Issue (Symptom) → Diagnosed Problem (Root Cause)
→ Researchable Problem (Scoped) → Measurable Variable (Operationalized)
```

### Topic ≠ Problem ≠ Research Problem

| Level | Contoh | Status |
|-------|--------|--------|
| **Topik** | Keamanan IoT | Terlalu luas, tidak bisa diuji |
| **Problem** | MQTT tidak terenkripsi | Spesifik tapi belum riset |
| **Research Problem** | Belum ada studi membandingkan overhead TLS 1.3 vs DTLS pada MQTT di IoT RAM < 64KB | Bisa dirancang eksperimennya |

### Symptom vs Root Cause

Apa yang diamati (gejala) ≠ mengapa terjadi (akar masalah). Gunakan **5 Whys** atau **Fishbone Diagram** untuk menggali.

Contoh: "User meninggalkan checkout" (symptom) → "Waktu loading > 8 detik karena API call sequential" (root cause).

### System Thinking

Setiap masalah riset TI harus terikat pada komponen sistem: **Input → Process → Output → Outcome → Constraints → Stakeholders**.

### Problem Quality Check

Masalah riset yang layak harus memenuhi 5 kriteria:
- **Clarity** — Satu orang membaca akan paham
- **Measurability** — Ada metrik kuantitatif
- **Relevance** — Penting untuk domain
- **Testability** — Bisa gagal (falsifiable)
- **Impact** — Ada kontribusi jika terjawab

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Menyelesaikan masalah (*solve*) | Memahami dan membuktikan (*understand & prove*) |
| Masalah | Bug, error, fitur belum ada | Gap dalam pengetahuan |
| Scope | Selesaikan semua yang perlu | Batasi agar bisa dibuktikan |
| Output | Working system | Evidence, paper, replicable findings |

### Istilah Penting

- **Problem Statement** — Formulasi tertulis: konteks sistem + gap + dampak + justifikasi
- **System Context** — Deskripsi lengkap: input, proses, output, outcome, constraints, stakeholders
- **Problem Drift** — Masalah "bermutasi" dari pendahuluan ke metodologi karena statement awal tidak presisi
- **Solution-First Thinking** — Memulai dari solusi tanpa masalah yang jelas — berbahaya dalam riset
- **Operational Definition** — Definisi variabel yang cukup jelas agar peneliti lain bisa mengukur hal yang sama

---

## Template A.2 — Problem Statement Builder

```
PROBLEM STATEMENT BUILDER

Domain & Konteks
  Domain   : E-Commerce / Sistem Informasi Bisnis / UMKM
  Konteks  : Pemanfaatan e-commerce oleh UMKM bermitra Grab di Kabupaten Garut untuk meningkatkan omzet

System Context
  Input       : Data kuesioner UMKM mitra Grab mengenai manfaat yang dirasakan, kapabilitas teknologi, tingkat adopsi e-commerce, dan peningkatan omzet
  Process     : Pengolahan data menggunakan metode kuantitatif dengan SEM-PLS
  Output      : Hasil analisis pengaruh e-commerce terhadap peningkatan omzet UMKM
  Outcome     : Diketahui faktor e-commerce yang paling berpengaruh terhadap peningkatan omzet UMKM
  Constraints : Sampel terbatas 100 responden, lokasi hanya di Kabupaten Garut, dan data berbasis persepsi responden
  Stakeholders: Pelaku UMKM, Grab, konsumen, peneliti, dan pihak pembina UMKM

Fenomena → Problem
  Fenomena yang diamati             : Penggunaan e-commerce pada UMKM meningkat, tetapi peningkatan omzet antar pelaku UMKM tidak selalu sama
  Gejala (symptom) yang terukur     : Masih ada UMKM yang kesulitan memahami strategi pemasaran digital dan belum mengalami peningkatan omzet optimal
  Masalah yang didiagnosis          : Pemanfaatan e-commerce belum optimal karena perbedaan kapabilitas teknologi, manfaat yang dirasakan, dan tingkat adopsi
  Masalah riset (researchable)      : Belum diketahui seberapa besar pengaruh manfaat yang dirasakan, kapabilitas teknologi, dan tingkat adopsi e-commerce terhadap peningkatan omzet UMKM bermitra Grab
  Variabel yang terukur             : Manfaat yang dirasakan, kapabilitas teknologi, tingkat adopsi, dan peningkatan omzet

Problem Quality Check
  [ ☑ ] Clarity — Apakah satu orang membaca akan paham?
  [ ☑ ] Measurability — Apakah ada metrik kuantitatif?
  [ ☑ ] Relevance — Apakah penting untuk domain?
  [ ☑ ] Testability — Apakah bisa gagal?
  [ ☑ ] Impact — Apakah ada kontribusi jika terjawab?

Problem Statement (1 paragraf):
    Pada UMKM yang bermitra dengan Grab di Kabupaten Garut, penggunaan e-commerce telah menjadi bagian penting dalam aktivitas pemasaran dan penjualan. Namun, tidak semua UMKM memperoleh peningkatan omzet yang sama karena masih terdapat kendala dalam memahami strategi pemasaran digital, memanfaatkan teknologi, dan mengadopsi e-commerce secara optimal. Oleh karena itu, penelitian ini bertujuan untuk menganalisis pengaruh manfaat yang dirasakan, kapabilitas teknologi, dan tingkat adopsi e-commerce terhadap peningkatan omzet UMKM, sehingga dapat diketahui faktor yang paling berpengaruh dalam mendukung peningkatan kinerja usaha.
```

---

## Latihan 1 — Dari Topik ke Masalah Riset

Pilih satu topik di bidang TI yang diminati. Transformasikan melalui 5 tahap Problem Formation Model.

**Topik awal:** Pengaruh e-commerce terhadap peningkatan omzet UMKM bermitra Grab

| Tahap | Hasil |
|-------|-------|
| Reality | UMKM bermitra Grab menggunakan e-commerce untuk menjangkau pasar yang lebih luas dan meningkatkan penjualan |
| Observed Issue (Symptom) | Tidak semua UMKM mengalami peningkatan omzet yang sama meskipun telah menggunakan e-commerce |
| Diagnosed Problem (Root Cause) | Kapabilitas teknologi, manfaat yang dirasakan, dan tingkat adopsi e-commerce pada tiap UMKM berbeda-beda |
| Researchable Problem | Belum diketahui seberapa besar pengaruh dimensi e-commerce terhadap peningkatan omzet UMKM bermitra Grab di Kabupaten Garut |
| Measurable Variable | Manfaat yang dirasakan, kapabilitas teknologi, tingkat adopsi, peningkatan omzet |

**Apakah terjebak solution-first thinking?** [ ] Ya / [ ☑ ] Tidak
> Jika ya, kembali ke tahap mana? Karena masalah dirumuskan dari fenomena penggunaan e-commerce dan kondisi omzet UMKM, bukan langsung dari solusi atau metode. 

---

## Latihan 2 — System Context Decomposition

Gambarkan konteks sistem dari masalah riset di Latihan 1.

| Komponen | Deskripsi |
|----------|----------|
| Input | Data primer dari kuesioner 100 responden UMKM mitra Grab |
| Process | Pengolahan data menggunakan pendekatan kuantitatif dan analisis SEM-PLS |
| Output | Nilai pengaruh variabel e-commerce terhadap peningkatan omzet |
| Outcome | Diperoleh bukti empiris tentang faktor yang memengaruhi peningkatan omzet UMKM |
| Constraints | Sampel terbatas, wilayah penelitian hanya Garut, data berasal dari persepsi responden |
| Stakeholders | Pelaku UMKM, Grab, konsumen, akademisi, dan pembina UMKM |

**Komponen mana yang paling relevan dengan masalah riset?** Process dan Constraints

---

## Latihan 3 — Problem Quality Check

Evaluasi problem statement yang sudah dibuat menggunakan 5 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Clarity | 4 | Masalah sudah jelas, namun masih bisa diperjelas pada batasan wilayah dan karakteristik UMKM |
| Measurability | 5 | Variabel diukur secara kuantitatif melalui indikator dan dianalisis dengan SEM-PLS |
| Relevance | 5 | Sangat relevan terhadap perkembangan UMKM digital dan e-commerce |
| Testability | 5 | Dapat diuji dengan hipotesis, kuesioner, dan analisis statistik |
| Impact | 4 | Memberikan manfaat praktis bagi UMKM, tetapi ruang lingkupnya masih lokal |

**Skor total:** 23 / 25

**Problem statement versi final (1 paragraf):**
> Penggunaan e-commerce pada UMKM bermitra Grab di Kabupaten Garut telah menjadi strategi penting dalam memperluas pasar dan meningkatkan penjualan, namun peningkatan omzet yang diperoleh tiap UMKM belum merata. Kondisi ini diduga disebabkan oleh perbedaan manfaat yang dirasakan, kapabilitas teknologi, dan tingkat adopsi e-commerce di antara pelaku UMKM. Oleh karena itu, penelitian ini bertujuan untuk menganalisis pengaruh ketiga faktor tersebut terhadap peningkatan omzet UMKM menggunakan pendekatan kuantitatif, sehingga dapat diketahui faktor yang paling dominan dalam mendukung peningkatan kinerja usaha. 

---

## Refleksi

> Bandingkan "masalah" yang biasa ditemui saat coding (bug, error) dengan masalah riset. Apa perbedaan fundamental dalam cara mendefinisikan dan mendekati keduanya?

**Jawaban:**
> Masalah dalam coding biasanya berupa bug atau error yang penyebabnya relatif langsung, misalnya kesalahan sintaks, logika program, atau integrasi sistem, sehingga fokus penyelesaiannya adalah memperbaiki agar sistem berjalan normal. Sedangkan masalah riset lebih berfokus pada fenomena yang belum sepenuhnya dipahami dan perlu dibuktikan secara ilmiah. Dalam riset, masalah harus dirumuskan secara sistematis, memiliki variabel yang terukur, dapat diuji, dan menghasilkan temuan yang dapat dipertanggungjawabkan. Jadi, coding lebih menekankan perbaikan teknis, sedangkan riset menekankan pembuktian ilmiah terhadap hubungan atau pengaruh antarvariabel. Berdasarkan WS-02, masalah riset memang harus melalui tahapan fenomena, gejala, akar masalah, hingga variabel terukur, bukan langsung ke solusi.
