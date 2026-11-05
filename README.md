# New York City Airbnb Market & Geographic Distribution Analysis

## Overview
Sebuah *dashboard* analitik interaktif yang dirancang untuk membedah pasar sewa jangka pendek Airbnb di New York City sepanjang tahun 2019[cite: 13]. Proyek ini mengubah data mentah katalog listing properti menjadi wawasan visual strategis guna memahami karakteristik tipe kamar, sebaran spasial wilayah, disparitas harga sewa, distribusi pencilan (*outliers*), hingga matriks keterkaitan antarvariabel operasional menggunakan **Tableau Desktop**.
<img width="1755" height="1240" alt="New York Dashboard_page-0001" src="https://github.com/user-attachments/assets/8abd0a2d-863c-421b-a90a-cd3975dc1389" />


---

## Business Questions Framework
Tabel berikut menguraikan pertanyaan bisnis dan analitik utama yang dijawab melalui visualisasi pada *dashboard*:

| Dimensi Analisis | Pertanyaan Bisnis Utama |
| :--- | :--- |
| **Preferensi Akomodasi** | • Berapa proporsi ketersediaan antara *Entire home/apt*, *Private room*, dan *Shared room* di pasar NYC |
| **Sebaran Spasial & Klaster** | • Bagaimana pola konsentrasi geografis sebaran properti di 5 wilayah utama (*boroughs*) New York City |
| **Disparitas Harga Antar Wilayah** | • Wilayah mana yang memegang rata-rata tarif sewa harian (*Average Price*) tertinggi dan terendah |
| **Distribusi & Outlier Harga** | • Bagaimana rentang interkuartil serta sebaran pencilan harga sewa (< $600) di tiap wilayah |
| **Segmentasi Anggaran Wisatawan** | • Bagaimana komposisi kelompok tarif (*Budget*, *Moderate*, *Expensive*, *Luxury*) terdistribusi secara komparatif per wilayah |

---

## Data Preparation & Calculated Fields (Tableau)
* **Penyelarasan Desimal Koordinat (`Latitude Plot` & `Longitude Plot`):** Mengatasi isu *locale* regional Windows yang membaca tanda titik sebagai ribuan dengan kalkulasi skalar numerik agar koordinat lintang dan bujur kembali ke format desimal yang valid.
* **Segmentasi Tarif Dinamis (`Kategori Harga`):** Mengelompokkan tarif numerik harian menjadi empat kelas pasar terstruktur melalui logika bersyarat (`Budget <= $75`, `Moderate 76–150`, `Expensive 151–300`, dan `Luxury > $300`).
* **Disaggregasi Data Geografis:** Menonaktifkan fitur *Aggregate Measures* pada analisis spasial untuk memetakan koordinat individual murni tanpa agregasi titik ringkasan.
* **Penyaringan Pencilan Ekstrem:** Mengaplikasikan filter ambang batas harga (< $600) guna mengeliminasi distorsi visual pada diagram kotak garis (*box plot*).

---

## Visualizations & Dashboard Layout (Tableau)
* **Tipe Ruangan (Bar Chart):** Diagram batang vertikal yang membedah ketersediaan tipe akomodasi, didominasi oleh *Entire home/apt* (25.409 listing) dan *Private room* (22.326 listing), berbanding kontras dengan *Shared room* (1.160 listing).
* **Peta Sebaran (Geographic Scatter Plot):** Plot koordinat multiwarna (*Longitude Plot* vs *Latitude Plot*) yang merekonstruksi siluet spasial 5 wilayah New York City secara akurat.
* **Rata-rata Harga (Horizontal Bar Chart):** Diagram pembanding nilai rata-rata tarif sewa harian (*Avg. Price*) per wilayah yang dipimpin Manhattan ($196.9), disusul Brooklyn, Staten Island, Queens, dan Bronx.
* **Heatmap Korelasi (Correlation Matrix Grid):** Matriks visualisasi sel persegi dengan gradasi warna divergen (*Red-Blue*) untuk memetakan interaksi metrik ketersediaan (*availability*), durasi sewa minimum, volume ulasan, dan harga.
* **Distribusi & Outlier Harga Sewa (Box-and-Whisker Plot):** Diagram kotak garis yang menampilkan nilai median, kuartil (*Q1 & Q3*), serta titik-titik pencilan (*outliers*) properti per wilayah hingga batas $600.
* **Perbandingan Kategori Harga di Setiap Wilayah (Side-by-Side Bar Chart):** Diagram batang komparatif berdampingan yang memetakan volume listing berdasarkan kelas anggaran (*Budget*, *Moderate*, *Expensive*, *Luxury*) di setiap wilayah New York.

---

## Key Business Insights
* **Dominasi Unit Privat:** Pasar properti New York didominasi mutlak oleh unit privat penuh (*Entire home/apt*) dan kamar privat (*Private room*), yang mencakup lebih dari 97% total listing, menandakan minimnya minat pasar terhadap akomodasi berbagi (*Shared room*).
* **Kekuatan Pasar Premium Manhattan:** Manhattan memimpin dalam perolehan rata-rata harga tertinggi ($196.9/malam) dengan persebaran pencilan harga mahal yang jauh lebih padat dibanding wilayah lain.
* **Peran Strategis Brooklyn:** Brooklyn menjadi penantang terdekat Manhattan dengan volume listing sangat tinggi, tetapi pasarnya bertumpu pada segmen harga menengah (*Moderate*) dan terjangkau (*Budget*).
* **Segregasi Wilayah Penyangga:** Wilayah Queens, Bronx, dan Staten Island mayoritas dihuni oleh unit listing berbiaya rendah (*Budget*), menyediakan alternatif hunian ekonomis dengan kepadatan listing yang lebih rendah.

---

## Strategic Recommendations
* **Standardisasi Fasilitas Premium di Manhattan:** Mengingat tingginya rata-rata harga dan dominasi segmen *Luxury*, platform dapat memperkuat program sertifikasi host bintang lima untuk memaksimalkan *Gross Merchandise Value* (GMV).
* **Ekspansi Penawaran Segmen Menengah di Brooklyn & Queens:** Mengoptimalkan pemasaran properti kelas menengah (*Moderate*) di area simpul transportasi guna menarik wisatawan yang mencari alternatif hemat biaya di luar pusat kota.
* **Pengembangan Potensi Host di Bronx & Staten Island:** Memberikan insentif dan program pembinaan bagi calon host di wilayah penyangga untuk meratakan suplai akomodasi wisata di seluruh penjuru kota.

---

## Tools Used
* **Google Colab (Python / Pandas):** Lingkungan komputasi berbasis *cloud* untuk eksplorasi awal dataset, pembersihan data (*data cleaning*), penanganan nilai kosong, dan validasi awal korelasi statistik.
* **Tableau Desktop:** Platform visualisasi utama untuk pembuatan *Calculated Fields*, penyesuaian sumbu (*axis scaling & tick marks*), pemetaan koordinat, hingga perakitan tata letak *grid dashboard* interaktif akhir.
* **Dataset:** `AB_NYC_2019.csv` (Data publik katalog properti Airbnb New York City 2019).
