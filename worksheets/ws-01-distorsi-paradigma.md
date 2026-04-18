# WS-01: Distorsi & Paradigma

> **Bab 1 — Research Mindset in IT**

---

## Ringkasan Materi

### Research Trust Model

Pengetahuan ilmiah tidak muncul langsung dari kenyataan. Ia melewati **6 tahap transformasi** yang masing-masing rawan distorsi:

```
Reality → Data → Processing → Analysis → Inference → Knowledge
```

Etika mencegah distorsi yang disengaja (fabrikasi, cherry-picking). Validitas mendeteksi distorsi yang tidak disengaja (confounding variable, sampling bias).

### Tiga Jenis Validitas

| Jenis | Pertanyaan | Contoh Ancaman |
|-------|-----------|----------------|
| **Internal Validity** | Apakah hubungan kausal benar ada? | Confounding variable |
| **External Validity** | Apakah bisa digeneralisasi? | Dataset terlalu homogen |
| **Construct Validity** | Apakah mengukur hal yang benar? | Metrik tidak sesuai klaim |

### Paradigma Riset

Mata kuliah ini menggunakan pendekatan **Positivist** (fenomena TI bisa diukur objektif melalui eksperimen terkontrol) diperkuat **Design Science Research** (artefak dibuat sebagai instrumen pengujian hipotesis, bukan tujuan akhir).

### Mode Berpikir Peneliti

**Curious** (mempertanyakan fenomena) → **Critical** (mengevaluasi klaim berdasarkan bukti) → **Systematic** (merancang investigasi terstruktur dan reproducible).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Membuat sistem yang bekerja | Menghasilkan pengetahuan yang valid |
| Pertanyaan khas | "Bagaimana membuatnya jalan?" | "Apakah klaim ini benar?" |
| Ukuran sukses | Sistem berfungsi, client puas | Hipotesis terjawab, temuan tervalidasi |
| Kegagalan | Harus dihindari | Harus dilaporkan (negative result = kontribusi) |

### Istilah Penting

- **Research Mindset** — Pola pikir yang menuntut bukti dan mempertanyakan asumsi
- **Research Ethics** — Prinsip perilaku: kejujuran, objektivitas, keterbukaan, akuntabilitas
- **HARKing** — Hypothesizing After Results are Known — merumuskan hipotesis setelah melihat data
- **Falsifiability** — Hipotesis harus bisa dibuktikan salah

---

## Template A.1 — Research Mindset Self-Assessment

```
Nama Peneliti    : Nunik Aulia Primadani
Tanggal          : 18 April 2026

1. Ketika membaca klaim "metode X 95% akurat":
   - Pertanyaan pertama saya: Apakah data yang digunakan cukup besar dan representatif?
   - Data yang dibutuhkan untuk verifikasi: Dataset yang digunakan, metode evaluasi (misalnya confusion matrix), ukuran sampel, serta kondisi eksperimen.

2. Posisi paradigma:
   - Pendekatan: [☑] Positivis  [ ] Interpretivis  [ ] Design Science  [ ] Mixed
   - Alasan: Karena penelitian menggunakan data kuantitatif, pengukuran objektif, dan analisis statistik (SEM-PLS) untuk menguji hubungan antar variabel, sehingga sesuai dengan paradigma positivis.
3. Identifikasi distorsi:
   - Asumsi tersembunyi: E-commerce dianggap sebagai faktor utama yang meningkatkan omzet tanpa mempertimbangkan faktor lain seperti kualitas produk, lokasi, atau strategi pemasaran.
   - Sumber bias potensial: Sampling bias (hanya UMKM mitra Grab di Garut), self-report bias dari kuesioner, serta kemungkinan confounding variable.
   - Langkah mitigasi: Menambah variasi sampel, menggunakan data objektif (misalnya data transaksi), serta memasukkan variabel kontrol dalam analisis.

4. Komitmen etika:
   - Data yang tidak akan dimanipulasi: Data hasil kuesioner dan hasil analisis statistik, termasuk data yang tidak mendukung hipotesis.
   - Batasan yang diakui sejak awal: Keterbatasan jumlah sampel, keterbatasan wilayah penelitian, dan kemungkinan adanya variabel lain yang tidak diteliti.
```

---

## Latihan 1 — Identifikasi Distorsi

Pilih satu paper riset di bidang TI yang mengklaim "metode X meningkatkan performa." Telusuri setiap tahap Research Trust Model.

**Paper yang dipilih:**
> Judul: Pengaruh E-Commerce Terhadap Peningkatan Omzet UMKM Bermitra Grab di Kabupaten Garut
> Penulis (Tahun): Lina Nurlaela & Fitri Syakinah (2025) 

| Tahap | Apa yang Dilakukan | Potensi Distorsi |
|-------|-------------------|-----------------|
| Reality → Data | Fenomena nyata yang ingin dijelaskan: apakah e-commerce meningkatkan omzet UMKM mitra Grab. Data dikumpulkan lewat kuesioner kepada 100 responden UMKM mitra Grab di Kabupaten Garut.  | Sampling bias: responden hanya UMKM mitra Grab di satu kabupaten, sehingga realitas UMKM yang tidak bermitra Grab atau di daerah lain tidak terwakili. |
| Data →  Processing	Data direkap, diuji validitas dan reliabilitas, lalu item dengan outer loading < 0,7 dieliminasi. | Processing bias / researcher degrees of freedom: penghapusan item bisa membuat model tampak lebih baik, tetapi berisiko menggeser konstruk awal jika tidak dijustifikasi kuat.|
| Processing → Analysis | Analisis memakai SEM-PLS dengan konstruk e-commerce dan peningkatan omzet; diuji outer model, inner model, R-square, f-square, bootstrapping. | Model specification bias: hubungan kompleks sosial-ekonomi disederhanakan menjadi model laten terbatas; variabel lain di luar model bisa memengaruhi omzet.|
| Analysis → Inference | Dari hasil statistik, penulis menyimpulkan e-commerce berpengaruh signifikan terhadap peningkatan omzet. | Causal overclaim: desainnya berbasis survei kuantitatif cross-sectional, sehingga lebih aman disebut “berhubungan signifikan” daripada “menyebabkan” secara kuat.|
| Inference → Knowledge | Hasil dibahas sebagai bukti bahwa penerapan e-commerce meningkatkan omzet UMKM. | External validity threat: temuan mungkin tidak dapat digeneralisasi ke UMKM non-Grab, sektor lain, atau wilayah lain.|

**Distorsi paling besar di tahap:**  Analysis → Inference

**Dua distorsi spesifik yang teridentifikasi:**
1. Confounding variable: omzet bisa dipengaruhi faktor lain seperti kualitas produk, lokasi, modal, promosi, musim penjualan, atau kondisi pasar, bukan hanya e-commerce.
2. Sampling bias: sampel terbatas pada 100 UMKM mitra Grab di Garut, sehingga generalisasi sangat terbatas.

---

## Latihan 2 — Analisis Kasus Etika

Skenario: Seorang peneliti menemukan bahwa jika 3 data point outlier dihapus, hasil eksperimennya menjadi signifikan. Dengan outlier, hasilnya tidak signifikan.

| Perspektif | Analisis |
|------------|---------|
| Kejujuran ilmiah |Peneliti tidak boleh menghapus outlier hanya agar hasil signifikan. Outlier hanya boleh dihapus bila ada alasan metodologis yang jelas, misalnya salah input, respon tidak valid, atau error pengukuran. |
| Transparansi | Kedua hasil sebaiknya dilaporkan: analisis dengan outlier dan tanpa outlier, berikut alasan penghapusan. Ini mencegah cherry-picking dan HARKing.  |
| Peer review | Reviewer kemungkinan akan mempertanyakan dasar penghapusan outlier. Jika alasan lemah, tindakan itu dapat dianggap manipulatif dan menurunkan kredibilitas penelitian. |

**Keputusan akhir dan justifikasi:**
> Outlier tidak boleh dihapus semata-mata untuk membuat hasil signifikan. Peneliti harus memeriksa dulu apakah outlier berasal dari kesalahan data atau memang bagian dari fenomena nyata. Jika outlier valid, maka hasil dengan outlier harus menjadi hasil utama. Jika ada analisis tanpa outlier, posisinya hanya sebagai analisis tambahan/sensitivitas, bukan alat untuk “memaksakan” hipotesis diterima.

---

## Latihan 3 — Posisi Paradigma

**Topik riset:** Pengaruh penggunaan e-commerce terhadap peningkatan omzet UMKM mitra Grab di Kabupaten Garut.

| Kriteria | Positivis | Interpretivis | Design Science |
|----------|-----------|---------------|----------------|
| Kesesuaian dengan topik (1–5) | 5 | 2 | 2 |
| Jenis data yang dikumpulkan | Data kuantitatif, kuesioner, indikator terukur, uji statistik | Narasi pengalaman pelaku UMKM, wawancara mendalam, makna subjektif penggunaan e-commerce | Artefak/sistem baru, prototipe platform, evaluasi solusi |
| Limitasi paradigma | Sulit menangkap makna subjektif dan konteks sosial yang kaya | Sulit memberi bukti hubungan kuantitatif yang kuat | Tidak relevan jika penelitian tidak membangun artefak baru |

**Paradigma yang dipilih:** Positivis
**Alasan:** Topik ini paling cocok dengan paradigma positivis karena fokusnya menguji hubungan antarvariabel yang terukur secara objektif menggunakan kuesioner dan SEM-PLS. Ini sejalan dengan materi bahwa pendekatan positivist digunakan saat fenomena TI diukur objektif melalui prosedur terstruktur.

---

## Refleksi

> Sebelum membaca materi ini, apakah pernah mempertanyakan klaim "95% akurat"? Setelah memahami rantai distorsi, pertanyaan apa yang sekarang akan diajukan saat membaca paper?

**Jawaban:**
> Sebelum memahami materi ini, klaim seperti “metode X 95% akurat” mungkin langsung dianggap kuat. Setelah memahami rantai distorsi, pertanyaan yang harus diajukan menjadi lebih kritis: 95% akurat berdasarkan data apa, pada konteks apa, diukur dengan metrik apa, dibandingkan dengan baseline apa, dan apakah hasilnya valid serta bisa digeneralisasi?
> Untuk paper ini, saya juga akan bertanya: apakah benar e-commerce menyebabkan kenaikan omzet, atau hanya berkorelasi dengan kenaikan omzet? Apakah sampel 100 UMKM mitra Grab di Garut cukup mewakili UMKM secara umum? Apakah konstruk “peningkatan omzet” benar-benar diukur secara objektif, atau hanya berdasarkan persepsi responden dalam kuesioner?
