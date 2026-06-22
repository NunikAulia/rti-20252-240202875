# WS-06: System-Experiment Mapping

> **Bab 6 — System Design sebagai Experimental Artifact**

---

## Ringkasan Materi

### Sistem = Instrumen Pengujian, Bukan Produk

Seorang engineer bertanya "apakah sistem bekerja?" — seorang peneliti bertanya "apa yang bisa dibuktikan sistem ini?" Sistem dalam riset adalah **artifact** — objek yang sengaja dibuat untuk menguji klaim spesifik.

### System as Experiment Model

```
RQ → Variable → System Component → Experimental Setup → Output
```

Setiap komponen sistem harus bisa ditelusuri ke variabel riset (top-down), dan setiap pengukuran harus menjawab RQ (bottom-up).

### Mapping Variabel ke Komponen

| Tipe Variabel | Peran di Sistem | Contoh |
|---------------|----------------|--------|
| **IV** (Independent) | Modul yang bisa di-toggle/swap | Algoritma A vs B |
| **DV** (Dependent) | Modul pengukuran | Logger, metrics collector |
| **CV** (Control) | Config yang dikunci | Dataset, parameter tetap |

Jika variabel tidak bisa di-map ke komponen apapun → arsitektur perlu didesain ulang.

### 4 Prinsip Desain Eksperimental

| Prinsip | Pertanyaan Kunci |
|---------|-----------------|
| **Traceability** | Komponen ini melayani variabel yang mana? |
| **Modularity** | Bisakah IV diubah tanpa memengaruhi yang lain? |
| **Controllability** | Apakah CV dieksternalisasi ke config file? |
| **Measurability** | Apakah sistem otomatis menghasilkan data yang dibutuhkan? |

### Variable Isolation melalui Arsitektur

- **Modular architecture** — Pisahkan berdasarkan variabel
- **Configuration-driven** — Ubah config (YAML/JSON), bukan code
- **Feature toggles** — On/off flag untuk ablation study

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan sistem | Memenuhi kebutuhan user | Menguji hipotesis, menghasilkan bukti |
| Arsitektur | Optimasi performa & skalabilitas | Optimasi isolasi variabel & reprodusibilitas |
| Konfigurasi | Sering hardcoded | Dieksternalisasi ke config file |
| Fitur tambahan | Menambah nilai user | Menambah noise jika tidak terkait RQ |

### Istilah Penting

- **Artifact** — Objek yang sengaja dibuat untuk memecahkan masalah atau menguji proposisi
- **Traceability** — Kemampuan menelusuri hubungan RQ → variabel → komponen → output
- **Variable Isolation** — Mengubah hanya satu variabel sambil menahan yang lain konstan
- **Ablation Study** — Menguji kontribusi tiap komponen dengan melepasnya satu per satu
- **Configuration-driven Execution** — Semua parameter di config file, bukan hardcoded

---

## Template A.6 — Mapping RQ ke Arsitektur Sistem

```
SYSTEM-EXPERIMENT MAPPING

Research Question: Bagaimana pengaruh e-commerce terhadap peningkatan omzet UMKM yang bermitra dengan Grab?

Variable → Component Mapping:
| Variabel | Tipe | Komponen Sistem | Cara Manipulasi/Pengukuran |
|----------|------|-----------------|---------------------------|
| E-commerce (manfaat, kapabilitas teknologi, adopsi)   | IV   | Modul kuesioner & input responden  | Mengubah indikator pada kuesioner             |
| Peningkatan omzet UMKM                                 | DV   | Modul analisis SEM-PLS             | Mengukur nilai R-square, t-statistic, f-square |
| Jumlah responden, metode SEM-PLS, objek penelitian     | CV   | Config penelitian                  | Dijaga tetap selama penelitian                |

4 Prinsip Desain:
  [ ✓ ] Traceability — Setiap komponen bisa ditelusuri ke variabel
  [ ✓ ] Variable Isolation — IV bisa diubah tanpa mengubah CV
  [ ✓ ] Measurement Integration — Pengukuran DV built-in
  [ ✓ ] Reproducibility — Setup bisa direkonstruksi

Experimental Setup:
  Input data     : Data kuesioner 100 responden UMKM mitra Grab
  Parameter      : Variabel e-commerce dan peningkatan omzet
  Output format  : Nilai statistik SEM-PLS (R-square, f-square, t-statistic)
```

---

## Latihan 1 — Variable-to-Component Mapping

Gunakan RQ dan variabel dari WS-05. Petakan ke komponen sistem.

**RQ:** Bagaimana pengaruh e-commerce terhadap peningkatan omzet UMKM yang bermitra dengan Grab?

| Variabel | Tipe | Komponen Sistem | Cara Manipulasi / Pengukuran |
|----------|------|-----------------|---------------------------|
| *E-commerce* | *IV* | *Modul kuesioner* | *Mengubah indikator pertanyaan* |
| *Peningkatan omzet* | *DV* | *Modul analisis SEM-PLS* | *Mengukur hasil statistik* |
| *Jumlah responden & metode penelitian* | *CV* | *Config penelitian* | *Dijaga tetap selama eksperimen* |

**Apakah semua variabel bisa di-map?** [ ✓ ] Ya / [ ] Tidak
> Ya, karena seluruh variabel penelitian sudah memiliki komponen sistem masing-masing, baik untuk manipulasi variabel independen, pengukuran variabel dependen, maupun pengendalian variabel kontrol.

---

## Latihan 2 — 4 Prinsip Desain

Evaluasi desain sistem terhadap 4 prinsip.

| Prinsip | Status | Bukti / Penjelasan |
|---------|--------|-------------------|
| Traceability | *✅* |  Setiap variabel memiliki komponen sistem yang jelas |
| Modularity | *✅* | Variabel independen dapat diubah tanpa mengubah metode analisis |
| Controllability | *✅* | Jumlah responden dan metode SEM-PLS dikontrol tetap |
| Measurability | *✅* | Sistem menghasilkan output statistik otomatis |

**Prinsip mana yang paling sulit dipenuhi?** Measurability
**Strategi untuk mengatasinya:**
> Menggunakan software SmartPLS agar pengukuran otomatis, valid, dan reliabel.

---

## Latihan 3 — Ablation Study Planning

Jika sistem memiliki 3 komponen utama, rencanakan ablation study.

| Kondisi | Komponen A | Komponen B | Komponen C | Hasil yang Diharapkan |
|---------|-----------|-----------|-----------|----------------------|
| Full | *✅ Manfaat yang dirasakan* | *✅ Kapabilitas teknologi* | *✅ Tingkat adopsi* | *Baseline penuh* |
| – A | *❌ (tanpa manfaat yang dirasakan)* | *✅* | *✅* | *Pengaruh omzet sedikit menurun* |
| – B | *✅* | *❌ (tanpa kapabilitas teknologi)*| *✅* | *Penurunan omzet paling besar* |
| – C | *✅* | *✅* | *❌ (tanpa tingkat adopsi)* | *Pengaruh omzet sedikit menurun* |

**Komponen mana yang diprediksi paling berkontribusi?** Kapabilitas teknologi
**Mengapa?**
> Karena berdasarkan hasil penelitian, kapabilitas teknologi memiliki nilai f-square paling tinggi sehingga memberikan pengaruh paling besar terhadap peningkatan omzet UMKM.

---

## Refleksi

> Apa risiko jika sistem dibangun seperti produk (monolitik, fitur lengkap) lalu baru dilakukan eksperimen? Mengapa arsitektur modular penting untuk riset?

**Jawaban:**
> Jika sistem dibangun seperti produk monolitik lalu baru dilakukan eksperimen, maka variabel penelitian akan sulit dipisahkan sehingga hasil penelitian kurang valid dan sulit dianalisis.
> Arsitektur modular penting dalam riset karena memudahkan isolasi variabel, mempermudah pengujian tiap komponen, dan membuat penelitian lebih reproducible.