# WS-15: Scientific Writing

> **Bab 15 — Penulisan Ilmiah**

---

## Ringkasan Materi

### Scientific Argument Flow

```
Problem → Gap → RQ → Method → Result → Analysis → Conclusion → Contribution
```

Paper ilmiah adalah **satu argumen utuh** dari masalah ke kontribusi. Setiap node harus terhubung logis ke node sebelum dan sesudahnya.

### Struktur IMRAD

| Section | Peran | Pertanyaan Kunci |
|---------|-------|-----------------|
| **Introduction** | Motivasi + frame | Why is this needed? |
| **Method** | Deskripsi (reproducible) | How was it done? |
| **Results** | Laporan objektif | What was found? |
| **Discussion** | Interpretasi + refleksi | What does it mean? |
| **Conclusion** | Ringkasan + kontribusi | So what? |

### Logical Flow — "Red Thread"

Setiap paragraf menjawab satu pertanyaan dan memicu pertanyaan berikutnya. Alur logis ini harus terasa di tiga level:
1. **Antar-kalimat** dalam paragraf
2. **Antar-paragraf** dalam section
3. **Antar-section** dalam paper

### Internal Consistency

Setiap elemen yang dijanjikan di Introduction harus hadir di Discussion/Conclusion.

**Consistency Matrix:**
```
           Intro  Method  Result  Discuss  Conclude
RQ1          ✓      ✓       ✓       ✓        ✓
RQ2          ✓      ✓       ✓       ✗ ←      ✓
Metrik-X     ✗      ✗       ✓ ←     ✗        ✗
```
**Masalah:** RQ2 dibahas di semua bagian kecuali Discussion. Metrik-X muncul di Result tapi tidak diperkenalkan di Method.

### Writing Quality Triad

| Kualitas | Deskripsi | Contoh Buruk → Baik |
|----------|----------|---------------------|
| **Clarity** | Dipahami sekali baca | "Performa meningkat" → "Accuracy meningkat dari 85.3% ke 89.7%" |
| **Precision** | Istilah eksak, tanpa ambiguitas | "signifikan" → "signifikan secara statistik (p=0.003, d=1.2)" |
| **Conciseness** | Setiap kata menambah informasi | Hapus kalimat redundan, filler words |

### Urutan Penulisan yang Disarankan

1. **Method & Results** — paling stabil, tulis pertama
2. **Discussion** — interpretasi berdasarkan hasil
3. **Introduction** — frame sesuai temuan aktual
4. **Abstract & Conclusion** — terakhir

### Target Jumlah Kata

| Section | Target |
|---------|--------|
| Introduction | 500–700 |
| Related Work | 700–1000 |
| Method | 800–1200 |
| Results | 500–800 |
| Discussion | 600–900 |
| Conclusion | 200–400 |

### Jebakan Kognitif

1. "Lebih panjang = lebih lengkap" → conciseness lebih berharga
2. "Introduction harus ditulis pertama" → justru ditulis terakhir
3. "Jargon teknis = lebih ilmiah" → clarity lebih penting
4. "Discussion = ringkasan Results" → Discussion = interpretasi + konteks

---

## Template A.15 — Paper Structure Checklist

```
PAPER STRUCTURE CHECKLIST

Title   : Analisis Pengaruh Manfaat yang Dirasakan, Kapabilitas Teknologi, dan Tingkat Adopsi E-Commerce terhadap Peningkatan Omzet UMKM Bermitra Grab di Kabupaten Garut
Target  : [ ☑ ] Jurnal  [ ] Konferensi  [ ] Laporan

Section Check:
  [ ☑ ] Abstract — masalah, metode, hasil utama, kontribusi (max 250 kata)
  [ ☑ ] Introduction — konteks → gap → RQ → kontribusi → struktur paper
  [ ☑ ] Related Work — concept-centric, gap positioning
  [ ☑ ] Method — reproducible: desain, variabel, metrik, setup, prosedur
  [ ☑ ] Results — tabel + grafik + observasi (tanpa interpretasi)
  [ ☑ ] Discussion — interpretasi, perbandingan, implikasi, limitation
  [ ☑ ] Conclusion — jawaban RQ, kontribusi, future work

Consistency Matrix:
  [ ☑ ] RQ di Introduction = RQ di Method = RQ di Conclusion
  [ ☑ ] Variabel di Method = variabel di Results
  [ ☑ ] Klaim di Discussion didukung data di Results
  [ ☑ ] Limitasi di Discussion di-address di Conclusion/Future Work

Writing Quality:
  [ ☑ ] Clarity — mudah dipahami tanpa re-read
  [ ☑ ] Precision — tidak ada istilah ambigu
  [ ☑ ] Conciseness — tidak ada kalimat redundan
```

---

## Latihan 1 — Paper Outline

Buat outline paper untuk riset Anda menggunakan struktur IMRAD.

| Section | Konten Utama (2-3 kalimat) | Target Kata |
|---------|---------------------------|------------|
| Abstract | Penelitian ini menganalisis pengaruh manfaat yang dirasakan, kapabilitas teknologi, dan tingkat adopsi e-commerce terhadap peningkatan omzet UMKM bermitra Grab di Kabupaten Garut. Penelitian menggunakan pendekatan kuantitatif dengan metode SEM-PLS. Hasil diharapkan menunjukkan faktor-faktor yang paling berpengaruh terhadap peningkatan omzet UMKM. | 200–250 |
| Introduction | Menjelaskan perkembangan digitalisasi UMKM dan pentingnya adopsi e-commerce dalam meningkatkan daya saing. Research gap menunjukkan masih terbatasnya penelitian yang menguji ketiga variabel tersebut secara simultan pada UMKM mitra Grab di Kabupaten Garut. | 500–700 |
| Related Work | Mengulas teori Technology Acceptance Model (TAM), kapabilitas teknologi, adopsi e-commerce, serta penelitian terdahulu mengenai peningkatan omzet UMKM melalui transformasi digital. | 700–1000 |
| Method | Menggunakan pendekatan kuantitatif dengan survei kepada UMKM bermitra Grab. Analisis data dilakukan menggunakan SEM-PLS melalui SmartPLS untuk menguji validitas, reliabilitas, dan hubungan antar variabel. | 800–1200 |
| Results | Menyajikan hasil pengujian outer model, inner model, nilai R², path coefficient, t-statistic, p-value, serta effect size setiap hipotesis penelitian. | 500–800 |
| Discussion | Menginterpretasikan pengaruh masing-masing variabel terhadap peningkatan omzet UMKM, membandingkan hasil dengan penelitian sebelumnya, serta menjelaskan implikasi praktis bagi pelaku UMKM dan Grab. | 600–900 |
| Conclusion | Menyimpulkan hasil penelitian, menjawab rumusan masalah, menjelaskan kontribusi penelitian terhadap pengembangan UMKM digital, serta memberikan rekomendasi penelitian selanjutnya. | 200–400 |

---

## Latihan 2 — Consistency Matrix

Buat consistency matrix untuk memverifikasi internal consistency paper Anda.

|  | Intro | Method | Result | Discussion | Conclusion |
|--|-------|--------|--------|-----------|-----------|
| RQ1 | ✓ | ✓ | ✓ | ✓ | ✓ |
| RQ2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| Metrik utama | ✓ | ✓ | ✓ | ✓ | ✓ |
| Variabel IV | ✓ | ✓ | ✓ | ✓ | ✓ |
| Variabel DV | ✓ | ✓ | ✓ | ✓ | ✓ |
| Klaim/kontribusi | ✓ | ✓ | ✓ | ✓ | ✓ |

**Isi setiap sel:** ✓ (ada & konsisten), ✗ (missing), ~ (ada tapi inkonsisten)

**Inkonsistensi yang ditemukan:**
> Tidak ditemukan inkonsistensi. Semua research question, variabel, metode, dan hasil telah konsisten pada setiap bagian paper.

**Tindakan perbaikan:**
> Memastikan setiap hasil statistik pada bagian Results dijelaskan implikasinya pada bagian Discussion dan dirangkum kembali pada bagian Conclusion.

---

## Latihan 3 — Writing Quality Check

Ambil satu paragraf dari tulisan Anda (atau tulis paragraf baru) dan evaluasi kualitasnya.

**Paragraf asli:**
> (tempel paragraf Anda di sini)

| Kriteria | Evaluasi | Perbaikan |
|----------|---------|-----------|
| Clarity | Kalimat terlalu umum dan terdapat pengulangan istilah "penggunaan e-commerce". | Menjelaskan manfaat secara spesifik terhadap peningkatan omzet dan daya saing UMKM. |
| Precision | Tidak menyebutkan variabel penelitian maupun hasil yang diukur. | Menambahkan variabel manfaat yang dirasakan, kapabilitas teknologi, dan adopsi e-commerce. |
| Conciseness | Terdapat kalimat yang redundan dan dapat dipadatkan. | Menggabungkan ide menjadi satu paragraf yang lebih efektif. |

**Paragraf setelah perbaikan:**
> Penelitian ini menunjukkan bahwa manfaat yang dirasakan, kapabilitas teknologi, dan tingkat adopsi e-commerce berkontribusi terhadap peningkatan omzet UMKM bermitra Grab di Kabupaten Garut. Optimalisasi teknologi digital memungkinkan pelaku UMKM memperluas jangkauan pasar, meningkatkan efisiensi operasional, serta memperkuat daya saing usaha di era ekonomi digital.
---

## Refleksi

> Apa perbedaan antara menulis "tentang" riset dan menulis sebagai "argumen" riset? Bagaimana urutan penulisan (Method → Discussion → Introduction) mengubah kualitas tulisan?

> Menulis **tentang** riset hanya mendeskripsikan proses penelitian yang dilakukan, sedangkan menulis sebagai **argumen** riset menyusun alur logis mulai dari permasalahan, research gap, rumusan masalah, metode, hasil, hingga kontribusi ilmiah. Dengan menulis menggunakan urutan **Method → Results → Discussion → Introduction → Conclusion**, isi artikel menjadi lebih konsisten karena pendahuluan disusun berdasarkan hasil penelitian yang telah diperoleh. Pendekatan ini membantu menjaga keterkaitan antarbagian, memperkuat argumen ilmiah, dan meningkatkan kualitas keseluruhan paper.
