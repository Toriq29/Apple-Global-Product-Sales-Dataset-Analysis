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

Langkah pertama adalah menampilkan beberapa baris awal data menggunakan head() untuk memperoleh gambaran umum mengenai isi dataset, seperti format data, nama kolom, serta contoh nilai pada setiap variabel.

Selanjutnya dilakukan pengecekan struktur dataset menggunakan info() untuk mengetahui tipe data dari masing-masing atribut, jumlah data, serta mendeteksi adanya nilai yang tidak lengkap (missing values).

Selain itu, dilakukan juga identifikasi jumlah missing values pada setiap kolom menggunakan isnull().sum(). Tahapan ini bertujuan untuk memastikan kualitas data dan menentukan langkah preprocessing yang diperlukan sebelum masuk ke tahap analisis lebih lanjut.

Melalui proses ini, diperoleh pemahaman awal mengenai kondisi dataset sehingga dapat membantu dalam menentukan strategi analisis yang tepat pada tahap berikutnya.
