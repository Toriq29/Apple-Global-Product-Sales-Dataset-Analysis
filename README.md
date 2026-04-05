# Apple-Global-Product-Sales-Dataset-Analysis

Dalam era digital saat ini, data menjadi aset penting dalam pengambilan keputusan bisnis. Pada project ini, dilakukan analisis terhadap dataset Apple Global Product Sales Dataset untuk memahami performa penjualan produk Apple secara global serta mengidentifikasi faktor-faktor yang mempengaruhi pendapatan perusahaan.

Analisis ini bertujuan untuk menggali insight dari data penjualan, mulai dari tren penjualan, distribusi geografis, hingga pengaruh diskon terhadap revenue. Dengan pendekatan berbasis data, diharapkan hasil analisis ini dapat memberikan gambaran yang lebih jelas mengenai strategi bisnis yang efektif.

Cakupan analisis dalam project ini meliputi:
1. Analisis Penjualan (Sales Analysis) – untuk memahami pola dan volume penjualan produk
2. Analisis Revenue (Pendapatan) – untuk mengevaluasi kontribusi pendapatan dari berbagai segmen
3. Analisis Diskon – untuk melihat pengaruh diskon terhadap performa penjualan
4. Analisis Waktu (Time Series) – untuk mengidentifikasi tren dan pola musiman
5. Analisis Geografis – untuk mengetahui distribusi penjualan berdasarkan wilayah
6. Analisis Produk Detail – untuk membandingkan performa antar produk
7. Analisis Mata Uang – untuk memahami dampak variasi mata uang terhadap revenue
8. Analisis Korelasi (Advanced) – untuk mengidentifikasi hubungan antar variabel dalam dataset

Melalui analisis ini, diharapkan dapat ditemukan insight yang relevan untuk mendukung pengambilan keputusan strategis berbasis data serta meningkatkan pemahaman terhadap dinamika penjualan produk Apple di pasar global.

## Dataset Description
Dataset Apple Global Product Sales Dataset berisi informasi terkait transaksi penjualan produk Apple secara global. Setiap baris merepresentasikan satu transaksi penjualan dengan berbagai atribut yang mencakup informasi waktu, lokasi, produk, pelanggan, serta performa penjualan.

Berikut penjelasan masing-masing variabel dalam dataset:

🧾 Informasi Transaksi
- sale_id → ID unik untuk setiap transaksi penjualan
- sale_date → Tanggal terjadinya transaksi
- year → Tahun transaksi
- quarter → Kuartal (Q1, Q2, Q3, Q4)
- month → Bulan transaksi

🌍 Informasi Lokasi
- country → Negara tempat penjualan terjadi
- region → Wilayah dalam negara (misalnya Asia, Europe, dll)
- city → Kota tempat transaksi

📱 Informasi Produk
- product_name → Nama produk Apple (misalnya iPhone, iPad, MacBook)
- category → Kategori produk
- storage → Kapasitas penyimpanan (contoh: 128GB, 256GB)
- color → Warna produk

💰 Informasi Harga & Penjualan
- unit_price_usd → Harga satuan produk dalam USD sebelum diskon
- discount_pct → Persentase diskon yang diberikan (%)
- units_sold → Jumlah unit yang terjual
- discounted_price_usd → Harga setelah diskon dalam USD
- revenue_usd → Total pendapatan dalam USD

💱 Informasi Mata Uang
- currency → Mata uang lokal transaksi
- fx_rate_to_usd → Nilai tukar mata uang lokal terhadap USD
- revenue_local_currency → Pendapatan dalam mata uang lokal

🛒 Informasi Transaksi & Pembayaran
- sales_channel → Kanal penjualan (online / offline)
- payment_method → Metode pembayaran (kartu kredit, transfer, dll)

👤 Informasi Pelanggan
- customer_segment → Segmentasi pelanggan (misalnya premium, regular)
- customer_age_group → Kelompok usia pelanggan
- previous_device_os → Sistem operasi perangkat sebelumnya (Android/iOS)
- customer_rating → Rating atau kepuasan pelanggan terhadap produk
- return_status → Status pengembalian produk (returned / not returned)

## Dataset Understanding
Pada tahap ini dilakukan eksplorasi awal terhadap dataset Apple Global Product Sales Dataset untuk memahami struktur, karakteristik, serta kualitas data sebelum dilakukan analisis lebih lanjut.

### Top 5 Data

Langkah pertama adalah menampilkan beberapa baris awal data menggunakan head() untuk memperoleh gambaran umum mengenai isi dataset, seperti format data, nama kolom, serta contoh nilai pada setiap variabel.

![Top 5 Data](Images/top_5_data_1.png)

![Top 5 Data](Images/top_5_data_2.png)
<br>
<br>
<br>
### Data Info

Selanjutnya dilakukan pengecekan struktur dataset menggunakan info() untuk mengetahui tipe data dari masing-masing atribut, jumlah data, serta mendeteksi adanya nilai yang tidak lengkap (missing values).

![Data Info](Images/data_info.png)

Berdasarkan hasil pengecekan, diketahui bahwa dataset memiliki beberapa tipe data, yaitu object (string), integer, dan float. Perbedaan tipe data ini akan disesuaikan kembali pada tahap preprocessing apabila diperlukan, agar sesuai dengan kebutuhan analisis dan memastikan hasil yang lebih akurat.
<br>
<br>
<br>
### Data Null

Selain itu, dilakukan juga identifikasi jumlah missing values pada setiap kolom menggunakan isnull().sum(). Tahapan ini bertujuan untuk memastikan kualitas data dan menentukan langkah preprocessing yang diperlukan sebelum masuk ke tahap analisis lebih lanjut.

![Data Null](Images/data_is_null_sum.png)

Berdasarkan hasil pengecekan, terdapat beberapa kolom yang memiliki nilai kosong (missing values), yaitu:
- storage : 4.804 data
- previous_device_os : 8.056 data
- customer_rating : 3.360 data

Keberadaan missing values pada kolom-kolom tersebut akan ditangani pada tahap data cleaning dengan metode yang sesuai, guna memastikan data yang digunakan dalam analisis lebih akurat dan representatif.
<br>
<br>
<br>
### Data Duplikasi
Selain itu, dilakukan juga pengecekan terhadap data duplikat menggunakan duplicated().sum() untuk memastikan tidak terdapat data yang terduplikasi yang dapat mempengaruhi hasil analisis.

![Data Duplicate](Images/jumlah_duplikasi.png)

Berdasarkan hasil pengecekan, tidak ditemukan adanya data duplikat dalam dataset. Dengan demikian, tidak diperlukan tindakan lebih lanjut terkait penanganan duplikasi data.
<br>
<br>
<br>
### Statistical Summary
Selanjutnya, dilakukan analisis statistik deskriptif menggunakan describe() untuk memahami distribusi data serta mengidentifikasi potensi outlier pada variabel numerik.

![Data Describe](Images/data_describe.png)
Berdasarkan hasil analisis statistik deskriptif, ditemukan adanya perbedaan yang signifikan antara nilai maksimum dan median pada beberapa variabel, yang mengindikasikan keberadaan nilai ekstrem (outlier) yang berpotensi mempengaruhi hasil analisis.

Secara lebih rinci, temuan pada masing-masing variabel adalah sebagai berikut:
1. unit_price_usd

Nilai maksimum tercatat sebesar 7.551, yang jauh lebih tinggi dibandingkan nilai median. Perbedaan yang signifikan ini mengindikasikan adanya outlier pada harga produk.
Meskipun hal ini masih memungkinkan karena adanya produk high-end (misalnya perangkat dengan spesifikasi tinggi), selisih yang terlalu besar tetap perlu ditinjau lebih lanjut untuk memastikan validitas data.

2. revenue_usd

Nilai maksimum mencapai 59.529, dengan selisih yang sangat besar dibandingkan nilai median. Hal ini menunjukkan adanya outlier yang kuat (strong outlier), yang kemungkinan disebabkan oleh transaksi dengan jumlah pembelian besar atau anomali dalam data.

3. fx_rate_to_usd

Ditemukan nilai maksimum sebesar 24.500, yang sangat tidak proporsional dibandingkan nilai median. Kondisi ini merupakan indikasi kuat adanya anomali (red flag), karena nilai tukar terhadap USD umumnya tidak berada pada rentang tersebut dalam konteks normal.

4. revenue_local_currency

Nilai maksimum mencapai 507 juta, yang menunjukkan perbedaan ekstrem dibandingkan nilai tengahnya. Nilai ini kemungkinan dipengaruhi oleh tingginya nilai pada variabel fx_rate_to_usd, sehingga terdapat keterkaitan antar variabel yang memperkuat indikasi adanya outlier.


Secara keseluruhan, keberadaan outlier pada variabel-variabel tersebut perlu ditangani pada tahap data cleaning, baik melalui validasi data, transformasi, maupun metode penanganan outlier lainnya, agar hasil analisis menjadi lebih akurat dan representatif.
<br>
<br>
<br>

Melalui proses ini, diperoleh pemahaman awal mengenai kondisi dataset sehingga dapat membantu dalam menentukan strategi analisis yang tepat pada tahap berikutnya.


