# Kimia Farma Business Performance Analytics (2020-2023)
> **Project-Based Internship: Big Data Analytics Virtual Internship x Rakamin Academy**
Project ini berfokus pada pengolahan, manipulasi, dan visualisasi data kinerja bisnis PT Kimia Farma Tbk dari tahun 2020 hingga 2023. Tujuan utamanya adalah menggabungkan beberapa sumber data operasional menjadi satu data mart/tabel analisa terpusat menggunakan SQL di Google BigQuery, lalu memvisualisasikannya ke dalam dashboard interaktif menggunakan Google Looker Studio guna menghasilkan data-driven insight untuk kebutuhan bisnis.

## Tech Stack & Tools
- **Data Warehouse / Database:** Google BigQuery
- **Language:** SQL (Standard SQL)
- **Data Visualization:** Google Looker Studio

## Dataset & Arsitektur Data
Project ini menggunakan 4 dataset mentah (format `.csv`) yang di-import ke Google BigQuery:
1. `kf_final_transaction`: Data riwayat transaksi penjualan obat.
2. `kf_product`: Data master produk/obat beserta harganya.
3. `kf_kantor_cabang`: Data master lokasi dan rating kantor cabang Kimia Farma.
4. `kf_inventory`: Data stok obat di masing-masing cabang.

Keempat tabel tersebut di-join menggunakan klausa `LEFT JOIN` untuk menghasilkan tabel agregasi akhir bernama **`tabel_analisa`**.

## Logika Bisnis & Perhitungan Metrik
Dalam membuat `tabel_analisa`, diterapkan beberapa kalkulasi dan logika bisnis wajib:
- **Persentase Gross Laba:** Ditentukan berdasarkan rentang harga produk (`price`):
  - Harga <= Rp 50.000 $\rightarrow$ Laba 10%
  - Harga > Rp 50.000 s.d Rp 100.000 $\rightarrow$ Laba 15%
  - Harga > Rp 100.000 s.d Rp 300.000 $\rightarrow$ Laba 20%
  - Harga > Rp 300.000 s.d Rp 500.000 $\rightarrow$ Laba 25%
  - Harga > Rp 50.0000 $\rightarrow$ Laba 30%
- **Nett Sales:** Diperoleh dari harga produk dikurangi persentase diskon yang diberikan.
- **Nett Profit:** Diperoleh dari nilai `Nett Sales` dikalikan dengan `Persentase Gross Laba`.

## Fitur Dashboard (Looker Studio)
Dashboard dirancang interaktif dengan visualisasi utama sebagai berikut:
1. **Filter Kontrol:** Saringan data berdasarkan Tahun, Provinsi, dan Kota.
2. **Scorecard KPI:** Menampilkan Total Revenue (Nett Sales), Total Profit, dan Total Unik Transaksi.
3. **Trend Line/Bar Chart:** Perbandingan Pendapatan Kimia Farma dari Tahun ke Tahun (2020-2023).
4. **Top 10 Geografis:** Grafik kepuasan wilayah berdasarkan Provinsi dan Total Transaksi.
5. **Geo Chart Profit:** Peta sebaran keuntungan (*Nett Profit*) di wilayah Indonesia.
6. **Anomali Analisis Tabel:** Menampilkan Top 5 Cabang dengan rating toko tinggi dari pusat, namun memiliki rating kepuasan transaksi terendah dari konsumen.

## 📂 Link Proyek
- **Google Looker Studio Dashboard:** [https://datastudio.google.com/reporting/360c5ebb-4344-45d5-9d72-65e9faaf1722]
- **Video Presentasi Proyek:** [GANTI_DENGAN_LINK_VIDEO_PRESENTASI_KAMU]
