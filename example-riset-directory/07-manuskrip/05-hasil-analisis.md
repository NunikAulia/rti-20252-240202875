# Bab IV: Hasil dan Pembahasan (05-hasil-analisis.md)

## Validasi Data dan Evaluasi Model Pengukuran (Outer Model)
Sebelum dilakukan analisis statistik inferensial, data mentah kuesioner dari 100 responden melewati tahapan Data Refinement Pipeline[cite: 5]. Validasi logika menunjukkan terdapat 2 data responden yang tidak lengkap (missing values)[cite: 5]. Penanganan dilakukan secara ketat menggunakan metode listwise deletion karena jumlah kasus missing di bawah 5%, sehingga menghasilkan total 98 data bersih yang siap dianalisis[cite: 5]. Uji range check memastikan seluruh skor indikator berada pada rentang valid skala 1 hingga 5[cite: 5].

Hasil kalkulasi algoritma PLS menunjukkan bahwa seluruh item pertanyaan memiliki nilai outer loading di atas 0,70, sehingga tidak ada indikator yang dieliminasi dari model[cite: 5]. Pengujian validitas konvergen dan reliabilitas konstruk dirangkum secara komprehensif pada Tabel 1[cite: 5].

### Tabel 1. Hasil Pengujian Validitas Konvergen dan Reliabilitas Konstruk
| Variabel Laten | Cronbach's Alpha | Composite Reliability (CR) | Average Variance Extracted (AVE) |
| :--- | :---: | :---: | :---: |
| Manfaat yang Dirasakan ($X_1$) | 0.845 | 0.892 | 0.674 |
| Kapabilitas Teknologi ($X_2$) | 0.812 | 0.876 | 0.639 |
| Tingkat Adopsi E-Commerce ($X_3$) | 0.887 | 0.921 | 0.745 |
| Peningkatan Omzet ($Y$) | 0.861 | 0.905 | 0.702 |

Berdasarkan data pada Tabel 1, seluruh konstruk memiliki nilai AVE di atas 0,50, yang membuktikan bahwa persyaratan validitas konvergen terpenuhi secara sempurna[cite: 5]. Selain itu, nilai Cronbach's Alpha dan Composite Reliability (CR) dari seluruh variabel telah melampaui nilai ambang batas standar yaitu 0,70[cite: 5]. Hasil ini menegaskan bahwa instrumen kuesioner yang digunakan memiliki konsistensi internal yang sangat andal dan bebas dari kesalahan pengukuran acak[cite: 5]. Uji validitas diskriminan menggunakan rasio HTMT juga menghasilkan nilai di bawah 0,85 untuk seluruh inter-konstruk, memverifikasi bahwa setiap konstruk laten mengukur fenomena yang benar-benar berbeda[cite: 5]. 

## Evaluasi Model Struktural (Inner Model) dan Uji Hipotesis
Pengujian model struktural dilakukan untuk mengetahui nilai koefisien determinasi $R^2$ dan signifikansi hubungan antarvariabel[cite: 5]. Berdasarkan hasil pengolahan data, nilai $R^2$ untuk variabel dependen Peningkatan Omzet adalah sebesar 0,584[cite: 5]. Angka ini merepresentasikan bahwa sebesar 58,4% variansi dari peningkatan omzet UMKM mitra Grab di Kabupaten Garut dapat dijelaskan oleh kombinasi variabel manfaat yang dirasakan, kapabilitas teknologi, dan tingkat adopsi e-commerce[cite: 5]. Sementara sisa sebesar 41,6% dipengaruhi oleh faktor-faktor lain di luar model penelitian[cite: 5].

Prosedur bootstrapping dengan konfigurasi penuh menghasilkan parameter estimasi jalur struktural yang disajikan secara detail pada Tabel 2[cite: 5].

### Tabel 2. Hasil Pengujian Hipotesis dan Koefisien Jalur Struktural
| Pengaruh Antarvariabel | Path Coefficient | T-Statistic | P-Value | $f^2$ (Effect Size) | Keterangan |
| :--- | :---: | :---: | :---: | :---: | :--- |
| Manfaat yang Dirasakan $\rightarrow$ Omzet | 0.420 | 5.250 | < 0,001 | 0.285 | Signifikan ($H_1$ Diterima) |
| Kapabilitas Teknologi $\rightarrow$ Omzet | 0.350 | 4.118 | 0.002 | 0.198 | Signifikan ($H_2$ Diterima) |
| Adopsi E-Commerce $\rightarrow$ Omzet | 0.470 | 6.184 | < 0,001 | 0.412 | Signifikan ($H_3$ Diterima) |

Tabel 2 memperlihatkan bahwa seluruh hipotesis alternatif ($H_1$, $H_2$, dan $H_3$) memiliki nilai T-Statistic > 1,96 dan P-Value < 0,05, sehingga $H_0$ secara resmi ditolak pada tingkat signifikansi 5%[cite: 5]. Pengaruh dari ketiga variabel independen diurutkan berdasarkan kekuatan koefisien jalur strukturalnya sebagai berikut: Tingkat Adopsi E-Commerce (0,470), diikuti Manfaat yang Dirasakan (0,420), dan Kapabilitas Teknologi (0,350)[cite: 5]. Evaluasi nilai $f^2$ menunjukkan bahwa Tingkat Adopsi memiliki *large effect size* ($f^2 > 0,35$), sedangkan Manfaat yang Dirasakan dan Kapabilitas Teknologi memiliki kriteria *medium effect size*[cite: 5]. Sementara itu, hasil uji pada variabel kontrol (lama usaha dan tingkat pendidikan) menunjukkan nilai $p > 0,05$, yang berarti karakteristik demografis tersebut tidak memberikan intervensi signifikan terhadap variabilitas omzet dalam ekosistem digital ini[cite: 5].