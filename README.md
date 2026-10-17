# Visualisasi Data Kunjungan Wisata Jawa Timur 2025

Proyek mata kuliah **Data Visualization** yang mengeksplorasi dataset kunjungan objek wisata di Jawa Timur sepanjang tahun 2025 menggunakan **Python, Pandas, dan Matplotlib**.

- **Nama:** Rivaldo Candra Putra
- **NIM:** 2418059
- **Notebook (Google Colab):** [Buka di Colab](https://colab.research.google.com/drive/1eH6rRWQYZ9zoclo3tqT1UcwFFj2o6pMw?usp=sharing)

> **Catatan:** dataset ini **dibuat sendiri (data simulasi)** untuk latihan visualisasi, bukan data resmi. Pola yang terlihat hanya berlaku untuk dataset ini.

---

## Tujuan

1. Menggunakan dataset yang punya variabel numerik, kategorik, dan waktu yang bisa dianalisis secara visual.
2. Menerapkan beberapa teknik visualisasi yang sesuai dengan karakteristik data.
3. Memberi judul, label sumbu, legenda, dan keterangan yang informatif pada setiap grafik.
4. Menuliskan interpretasi (insight) untuk setiap visualisasi.
5. Menarik kesimpulan dari hasil eksplorasi dan visualisasi.

## Dataset

File: `data_kunjungan_wisata.xlsx` (100 baris, 10 kolom, 10 destinasi di 7 kota/kabupaten, Januari-Desember 2025).

| Kolom | Keterangan |
|---|---|
| `id_kunjungan` | Nomor identifikasi unik setiap catatan kunjungan |
| `tanggal` | Tanggal kunjungan |
| `destinasi` | Nama objek wisata |
| `kota` | Kota/kabupaten lokasi objek wisata |
| `jenis_wisata` | Gunung, Taman Rekreasi, Pantai, Air Terjun, Budaya & Sejarah |
| `jumlah_pengunjung` | Jumlah pengunjung pada hari tersebut |
| `harga_tiket` | Harga tiket masuk per orang (Rupiah) |
| `lama_kunjungan_jam` | Rata-rata lama kunjungan (jam) |
| `rating` | Penilaian pengunjung (skala 1-5) |
| `cuaca` | Cerah, Berawan, atau Hujan |

Kolom turunan yang dibuat di notebook:

- `bulan_kunjungan`: tahun-bulan dari `tanggal` (format `YYYY-MM`).
- `gmv`: `jumlah_pengunjung × harga_tiket`, yaitu nilai total tiket terjual per catatan.

## Alur Analisis

1. Import library dan load dataset.
2. Eksplorasi awal: `info()`, `isnull().sum()`, `describe()`, dan jumlah catatan per bulan.
3. Membuat kolom `bulan_kunjungan` dan `gmv`.
4. Agregasi GMV per bulan dengan `groupby` dan `sum`.
5. Membangun line chart bertahap (ukuran, judul, label, gaya garis, grid, anotasi), lalu versi finalnya.
6. Membuat visualisasi lain sesuai jenis datanya.
7. Menyusun dashboard ringkas dan kesimpulan.

## Visualisasi

| No | Jenis | Menjawab pertanyaan | Insight utama |
|---|---|---|---|
| 1 | Line chart | Bagaimana tren GMV bulanan? | GMV tertinggi Desember (Rp461 juta), terendah November (Rp160 juta), Juni puncak kedua (Rp379 juta) |
| 2 | Bar chart horizontal | Destinasi mana yang GMV-nya terbesar? | Jatim Park 2 dan Batu Secret Zoo menyumbang sekitar 84% GMV |
| 3 | Pie chart | Jenis wisata apa yang paling banyak dikunjungi? | Taman Rekreasi 52,2%, Gunung 28,2%, Pantai 10,6% |
| 4 | Histogram | Bagaimana sebaran rating? | Rata-rata 4,21; terbanyak pada rentang 4,2-4,6 |
| 5 | Scatter plot | Apakah harga tiket berhubungan dengan jumlah pengunjung? | Korelasi 0,59, tetapi belum tentu sebab-akibat |
| 6 | Box plot | Apakah cuaca memengaruhi jumlah pengunjung? | Median hujan 290, berawan 350, cerah 390 |
| 7 | Stacked bar | Bagaimana kontribusi tiap jenis wisata terhadap GMV bulanan? | Taman Rekreasi tampak menjadi penyumbang terbesar |
| 8 | Heatmap | Kapan dan di jenis wisata mana pengunjung memuncak? | Gunung pada Juli (2.800) dan Taman Rekreasi pada Desember (2.790) |
| 9 | Subplots (dashboard) | Ringkasan empat grafik utama | Rata-rata pengunjung terendah saat hujan (286) |

Setiap grafik memiliki judul, label sumbu, dan legenda bila diperlukan. Warna jenis wisata memakai satu kamus `warna_jenis` agar konsisten di pie chart, scatter plot, dan stacked bar.

## Kesimpulan

- Total GMV sepanjang 2025 sekitar **Rp3,42 miliar**.
- GMV memuncak pada Desember dan terendah pada November.
- Dua destinasi (Jatim Park 2 dan Batu Secret Zoo) mendominasi GMV; Taman Rekreasi paling banyak dikunjungi.
- Hujan cenderung menurunkan jumlah pengunjung.

## Keterbatasan

- Data simulasi dengan hanya 100 baris, sehingga hasil hanya untuk latihan.
- `jumlah_pengunjung` adalah angka per hari dan jumlah catatan per bulan bisa berbeda, sehingga GMV bulanan sebaiknya dibaca bersama jumlah catatan (`groupby('bulan_kunjungan').size()`).
- Harga tiket tetap per destinasi, jadi korelasi harga dan pengunjung kemungkinan mencerminkan perbedaan jenis wisata.
- Kesimpulan yang sesungguhnya memerlukan data nyata (misalnya BPS atau Satu Data Jawa Timur) dengan jumlah lebih banyak.

## Cara Menjalankan

1. Buka notebook di [Google Colab](https://colab.research.google.com/drive/1eH6rRWQYZ9zoclo3tqT1UcwFFj2o6pMw?usp=sharing).
2. Unggah `data_kunjungan_wisata.xlsx` ke Google Drive, lalu sesuaikan path pada sel load dataset:
   ```python
   dataset = pd.read_excel('/content/drive/MyDrive/Colab Notebooks/data_kunjungan_wisata.xlsx')
   ```
3. Jalankan semua sel secara berurutan.

Untuk menjalankan secara lokal:

```bash
pip install pandas matplotlib openpyxl
```

Ganti bagian `google.colab` / `drive.mount` dengan path file lokal.

## Teknologi

- Matplotlib
- Google Colab
