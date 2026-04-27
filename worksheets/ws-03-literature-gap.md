# WS-03: Literature Mapping & Gap

> **Bab 3 — Literature Review, Research Gap & Baseline**

---

## Ringkasan Materi

### Literature Review = Positioning, Bukan Ringkasan

Literature review bukan merangkum paper satu per satu. Pendekatan yang benar adalah **concept-centric** — organisasi berdasarkan tema, metode, atau variabel. Tujuan: menemukan **pola, kontradiksi, dan gap**.

### Empat Jenis Research Gap

| Jenis Gap | Deskripsi | Contoh |
|-----------|----------|--------|
| **Performance Gap** | Performa belum memadai | Akurasi deteksi hanya 78% pada kasus tertentu |
| **Method Gap** | Pendekatan belum diterapkan | Belum ada yang pakai transformer untuk task ini |
| **Data Gap** | Dataset terbatas/tidak representatif | Semua studi pakai dataset sintetis |
| **Context Gap** | Belum diuji pada konteks berbeda | Belum ada evaluasi di negara berkembang |

Gap terkuat = kombinasi 2+ jenis.

### Systematic Search Strategy

1. **Database**: IEEE Xplore, ACM DL, Scopus, Google Scholar
2. **Boolean query** yang terdokumentasi eksplisit
3. **Snowballing**: backward (telusuri referensi) + forward (cari yang mengutip)
4. Klaim "belum ada penelitian" harus didukung **bukti pencarian**

### Baseline Selection — 3 Kriteria

| Kriteria | Pertanyaan |
|----------|-----------|
| **Relevan** | Apakah menyelesaikan masalah yang sama? |
| **Representatif** | Apakah mewakili common practice? |
| **State-of-the-Art** | Apakah terbaru/terbaik? |

Membandingkan deep learning 2024 dengan decision tree sederhana tanpa justifikasi = **straw man comparison** (perbandingan tidak jujur).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan baca literatur | Mencari solusi yang sudah ada | Memahami apa yang belum terjawab |
| Cara membaca paper | Tutorial, how-to | Metode, limitasi, gap |
| Baseline | Framework terpopuler | State-of-the-art yang rigorous |
| Dokumentasi pencarian | Tidak diperlukan | Wajib (reproducible) |

### Istilah Penting

- **Concept-centric** — Organisasi literatur berdasarkan konsep/metode, bukan per penulis
- **Snowballing** — Backward (telusuri referensi) + Forward (cari yang mengutip paper kunci)
- **Research Position** — Pernyataan eksplisit posisi riset terhadap studi sebelumnya
- **Straw man comparison** — Memilih baseline lemah agar metode sendiri terlihat lebih baik

---

## Template A.3 — Literature Mapping & Gap Identification

```
LITERATURE MAPPING

Topik      : Pengaruh E-Commerce terhadap Peningkatan Omzet UMKM
Database   : Google Scholar
Query      : "e-commerce UMKM omzet" AND "pengaruh e-commerce terhadap pendapatan UMKM"
Tahun      : 2019–2025
Hasil awal : 50 paper → Screening → ____ paper final

Literature Matrix (concept-centric):

| Study | Tahun | Method | Data | Result | Limitation |
|-------|-------|--------|------|--------|------------|
| Nurlaela & Syakinah   | 2025  | SEM-PLS      | 100 UMKM Garut          | E-commerce signifikan meningkatkan omzet | Hanya 1 daerah                 |
| Ikhsan & Hasan        | 2020  | Kuantitatif  | UMKM Makassar           | Penjualan meningkat                      | Sampel terbatas                |
| Rianty & Rahayu       | 2021  | Kuantitatif  | UMKM mitra Gojek        | Pendapatan meningkat                     | Fokus pandemi                  |
| Gustina et al.        | 2022  | Statistik    | UMKM Padang             | Dampak positif e-commerce                | Variabel terbatas              |
| Fathimah              | 2019  | Regresi      | UMKM Indonesia          | Adopsi meningkatkan kinerja usaha        | Tidak bahas teknologi detail   |

Pola yang ditemukan:
  Metode dominan     : Kuantitatif (SEM-PLS, regresi, statistik)
  Dataset umum       : UMKM pada wilayah tertentu (lokal)
  Limitasi berulang  : Sampel kecil, wilayah terbatas, variabel belum kompleks

GAP IDENTIFICATION

Gap 1: [Jenis: performance / method / data / context]
  Deskripsi    : Dataset penelitian terbatas pada wilayah tertentu sehingga hasil belum representatif secara luas
  Bukti        : Sebagian besar penelitian hanya menggunakan data UMKM di satu kota/daerah
  Signifikansi : Membatasi generalisasi hasil penelitian terhadap UMKM secara nasional

Gap 2: [Jenis: Context Gap]
  Deskripsi    : Penelitian belum banyak dilakukan pada berbagai konteks wilayah yang berbeda
  Bukti        : Studi hanya fokus pada daerah seperti Garut, Makassar, dan Padang
  Signifikansi : Perbedaan kondisi ekonomi dan teknologi tiap daerah dapat mempengaruhi hasil

Baseline Selection:
| Baseline | Relevansi | Representatif | Source |
|----------|-----------|---------------|--------|
| SEM-PLS        | Digunakan untuk analisis pengaruh e-commerce     | Banyak digunakan dalam studi UMKM    | Nurlaela (2025)        |
| Regresi Linier | Mengukur hubungan variabel ekonomi               | Metode umum dalam penelitian ekonomi | Fathimah (2019)        |
```

---

## Latihan 1 — Concept-Centric Literature Table

Gunakan topik riset dari WS-02. Cari minimal 5 paper relevan menggunakan Google Scholar atau database lain.

**Topik riset:** Pengaruh E-Commerce terhadap peningkatan omzet UMKM
**Query pencarian:** e-commerce UMKM omzet" AND "pendapatan UMKM
**Database:** Google Scholar

| # | Study | Tahun | Method | Dataset | Result | Limitasi |
|---|-------|-------|--------|---------|--------|----------|
| 1 | *Nurlaela & Syakinah* | *2025* | *SEM-PLS* | *100 UMKM Garut* | *Signifikan* | *Wilayah terbatas* |
| 2 | *Ikhsan & Hasan*| *2020* | *Kuantitatif* | *UMKM Makassar* | *Meningkat* |*Sampel kecil* |
| 3 | *Rianty & Rahayu* | *2021* | *Kuantitatif* | *UMKM Gojek* | *Naik* | *Fokus pandemi* |
| 4 | *Gustina et al.* | *2022* | *Statistik* | *UMKM Padang* | *Positif* | *Variabel sedikit* |
| 5 | *Fathimah* | *2019* | *Regresi* | *UMKM Indonesia* | *Kinerja naik* | *Tidak detail* |

**Pola yang terlihat — Metode dominan:** Metode kuantitatif
**Limitasi yang berulang:** Wilayah terbatas dan sampel kecil

---

## Latihan 2 — Gap Identification

Berdasarkan tabel di Latihan 1, identifikasi gap.

| Jenis Gap | Ditemukan? | Gap Statement |
|-----------|-----------|---------------|
| Performance Gap | [ ] Ya / [ ☑ ] Tidak | Tidak ditemukan pengukuran performa karena sebagian besar penelitian tidak menguji akurasi AI dalam diagnosis secara langsung |
| Method Gap | [ ☑ ] Ya / [ ] Tidak | Sebagian besar penelitian menggunakan metode kualitatif dan literature review, sehingga belum banyak penelitian empiris kuantitatif yang menguji penggunaan ChatGPT dalam self-diagnosis |
| Data Gap | [ ☑ ] Ya / [ ] Tidak | Data yang digunakan masih terbatas, seperti sampel kecil atau hanya berbasis literatur, sehingga kurang representatif |
| Context Gap | [ ☑ ] Ya / [ ] Tidak | Belum ada penelitian yang secara spesifik mengkaji penggunaan ChatGPT dalam self-diagnosis BPD pada mahasiswa |

**Gap utama yang dipilih:** Data Gap + Context Gap
**Mengapa gap ini penting (bukan sekadar "belum ada yang meneliti")?**
> Gap ini penting karena keterbatasan data dan konteks menyebabkan hasil penelitian tidak dapat digeneralisasi secara luas. Dengan memperluas dataset dan konteks penelitian, hasil yang diperoleh akan lebih akurat dan relevan untuk berbagai kondisi UMKM.

---

## Latihan 3 — Baseline Selection

Pilih 2 baseline dari literatur yang sudah dibaca.

| # | Baseline | Mengapa Relevan | Mengapa Representatif | Apakah SOTA? | Sumber |
|---|----------|----------------|----------------------|-------------|--------|
| 1 | SEM-PLS | Analisis hubungan variabel | Banyak digunakan | bukan | Nurlaela (2025) |
| 2 | Regresi Linier | Analisis pengaruh ekonomi | Metode umum | Tidak | Fathimah (2019) |

**Apakah pemilihan baseline ini bisa dianggap straw man?** [ ] Ya / [ ☑ ] Tidak
> Justifikasi:  Baseline yang digunakan merupakan metode umum dan relevan sehingga perbandingan tetap adil dan tidak bias.

---

## Refleksi

> Apa perbedaan antara "belum ada yang meneliti ini" (klaim tanpa bukti) dengan research gap yang valid? Bagaimana cara membuktikan bahwa sebuah gap benar-benar ada?

**Jawaban:**
> "belum ada yang meneliti ini” merupakan klaim tanpa bukti karena tidak didukung oleh pencarian literatur yang sistematis. Sedangkan research gap yang valid harus didasarkan pada analisis beberapa penelitian sebelumnya yang menunjukkan adanya keterbatasan atau kekurangan tertentu.
> Cara membuktikan adanya gap adalah dengan melakukan pencarian literatur secara sistematis, menggunakan database terpercaya, mendokumentasikan query pencarian, serta menunjukkan pola dan keterbatasan yang berulang dari penelitian yang telah ada. Dengan demikian, gap yang ditemukan dapat dipertanggungjawabkan secara ilmiah.
