# 04-data

Data mentah hasil pengumpulan kuesioner adopsi e-commerce pada UMKM mitra Grab — input untuk analisis SEM-PLS WS 11-14.

## Isi yang diharapkan

- Hasil respons kuesioner dalam format CSV (Konstruk Laten $X_1$, $X_2$, $X_3$, dan $Y$)
- Log distribusi kuesioner (channel, tanggal, jumlah responden per gelombang)
- Metadata validasi (status responden: valid/tidak valid, alasan eliminasi data)
- Ringkasan data (jumlah responden, periode, channel distribusi)

## Catatan

Data di folder ini bersifat mentah (*raw data*) hasil lapangan dan belum diolah ke dalam model pengukuran struktural. Hasil olahan statistik inferensial akhir (SmartPLS 4.0) disimpan di [../06-output/](../06-output/).

## Berkas

- [raw_kuesioner_umkm.csv](raw-kuesioner-umkm.csv.md) — data 100 responden masuk dari Google Form sebelum melewati proses *refinement pipeline*.
- [smartpls_metadata.json](smartpls-metadata-json.md) — konfigurasi lingkungan perangkat lunak, *random seed* 42, dan jejak audit *missing values*.

## Ringkasan Data

| Item | Nilai |
|------|-------|
| Total responden masuk | 100 |
| Responden lolos uji *Range Check* (1-5) | 100 |
| Responden dikeluarkan akibat data tidak lengkap (*Missing Values*) | 2 |
| Responden valid untuk analisis final SmartPLS | 98 |
| Periode pengumpulan data | April – Juni 2026 |
| Channel Distribusi | Google Form (grup komunitas merchant Grab Garut, kunjungan lapangan) |

## Log Distribusi Kuesioner

| Gelombang | Tanggal (2026) | Channel Distribusi | Target Responden | Jumlah yang Mengisi |
|-----------|----------------|--------------------|------------------|---------------------|
| 1 | 15–30 April | Grup WhatsApp Komunitas Merchant Grab | Pelaku UMKM mitra aktif di Garut | 42 |
| 2 | 01–15 Mei | Broadcast digital via perantara pihak ketiga | Pelaku UMKM jangkauan regional | 13 |
| 3 | 16–05 Juni | Kunjungan langsung (tatap muka / *field survey*) | Pelaku UMKM *offline* sentra kuliner Garut | 45 |
| **Total** | **April–Juni 2026** | — | — | **100** |

---

## Catatan Kanal Distribusi

- **Gelombang 1 (Online - Komunitas)** — Distribusi cepat melalui intervensi grup koordinasi merchant Grab. Mendapatkan respons instan karena pelaku usaha sudah terbiasa berinteraksi secara digital.
- **Gelombang 2 (Online - Media)** — Distribusi eksternal digital umum. Menghasilkan *engagement* yang relatif rendah karena tidak adanya hubungan kedekatan fungsional secara langsung.
- **Gelombang 3 (Offline - Lapangan)** — Pendekatan tatap muka langsung ke pelaku usaha (warung, depot, merchant kuliner lokal). Sangat efektif untuk membantu pelaku usaha yang memiliki keterbatasan waktu pengisian mandiri secara online.

---

## Variabel dan Konstruk yang Diukur

| Konstruk Laten | Kode | Indikator Pengukuran | Jumlah Item | Skala Pengukuran |
|----------------|------|----------------------|-------------|------------------|
| **Manfaat yang Dirasakan** | $X_1$ | Kejelasan utilitas digital, perluasan konsumen | 4 item (X1_1 - X1_4) | Likert 1–5 |
| **Kapabilitas Teknologi** | $X_2$ | Kesiapan infrastruktur, literasi, pengelolaan aplikasi | 4 item (X2_1 - X2_4) | Likert 1–5 |
| **Tingkat Adopsi E-Commerce** | $X_3$ | Intensitas eksploitasi fitur GrabMerchant | 4 item (X3_1 - X3_4) | Likert 1–5 |
| **Peningkatan Omzet UMKM** | $Y$ | Efisiensi profitabilitas, tren omzet finansial | 4 item (Y_1 - Y_4) | Likert 1–5 |
| *Variabel Kontrol (Demografi)* | — | Pengalaman industri (Lama Usaha) & Jenjang Pendidikan | 2 item | Nominal / Ordinal |

---

## Statistik Deskriptif Karakteristik Usaha (98 Responden Valid)

### 1. Berdasarkan Lama Berjalannya Usaha
| Durasi Usaha | Jumlah Responden | Persentase |
|--------------|------------------|------------|
| < 1 Tahun | 15 | 15.3% |
| 1 – 3 Tahun | 40 | 40.8% |
| 3 – 5 Tahun | 29 | 29.6% |
| > 5 Tahun | 14 | 14.3% |
| **Total** | **98** | **100%** |

### 2. Berdasarkan Tingkat Pendidikan Terakhir Pelaku Usaha
| Jenjang Pendidikan | Jumlah Responden | Persentase |
|--------------------|------------------|------------|
| SMP / Sederajat | 10 | 10.2% |
| SMA / Sederajat | 64 | 65.3% |
| Diploma / Sarjana | 24 | 24.5% |
| **Total** | **98** | **100%** |

---

## Anomali & Catatan Pembersihan Data (*Data Refinement Pipeline*)

- **Deteksi Missing Values:** Analisis logika data menemukan adanya kolom kosong tidak terisi pada **RESP_015** (item X1_3 dan Y_2) serta **RESP_062** (item X3_2 dan Y_4).
- **Eksekusi Penanganan:** Dikarenakan total kasus *missing data* bernilai sangat kecil (2.0% dari total populasi), penanganan dijalankan menggunakan prosedur **Listwise Deletion** (mengeklusi baris secara utuh dari pengujian SmartPLS).
- **Dataset Final:** Jumlah sampel bersih yang dievaluasi pada pemodelan jalur struktural adalah **98 sampel data**.

---

## Statistik Deskriptif Awal (100 Responden, Sebelum Filtering)

| Konstruk Variabel | Nilai Mean | Std. Deviasi | Nilai Minimum | Nilai Maksimum |
|-------------------|------------|--------------|---------------|----------------|
| **Manfaat yang Dirasakan ($X_1$)** | 4.12 | 0.62 | 2.00 | 5.00 |
| **Kapabilitas Teknologi ($X_2$)** | 3.88 | 0.71 | 2.00 | 5.00 |
| **Tingkat Adopsi E-Commerce ($X_3$)** | 4.28 | 0.55 | 2.00 | 5.00 |
| **Peningkatan Omzet UMKM ($Y$)** | 4.05 | 0.68 | 1.00 | 5.00 |