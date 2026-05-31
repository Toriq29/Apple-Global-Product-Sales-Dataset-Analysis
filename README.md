# 🍎 Apple Global Product Sales — Data Analysis

> Analisis dataset transaksi penjualan Apple secara global (2022–2024) untuk menggali insight strategis terkait performa produk, pasar, dan perilaku konsumen.

---

## 📋 Daftar Isi
- [Tentang Project](#tentang-project)
- [Dataset](#dataset)
- [Pipeline Analisis](#pipeline-analisis)
- [Data Understanding](#data-understanding)
- [Data Cleaning](#data-cleaning)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Key Insights](#key-insights)

---

## Tentang Project

Dalam era digital saat ini, data menjadi aset penting dalam pengambilan keputusan bisnis. Project ini menganalisis **Apple Global Product Sales Dataset** untuk memahami performa penjualan produk Apple secara global serta mengidentifikasi faktor-faktor yang memengaruhi pendapatan perusahaan.

**Tujuan:** Menggali insight yang relevan untuk mendukung pengambilan keputusan strategis berbasis data serta meningkatkan pemahaman terhadap dinamika penjualan produk Apple di pasar global.

---

## Dataset

Dataset mencakup transaksi penjualan Apple secara global pada **periode 2022–2024**. Setiap baris merepresentasikan satu transaksi dengan atribut berikut:

| Kategori | Variabel |
|---|---|
| 🧾 Transaksi | `sale_id`, `sale_date`, `year`, `quarter`, `month` |
| 🌍 Lokasi | `country`, `region`, `city` |
| 📱 Produk | `product_name`, `category`, `storage`, `color` |
| 💰 Harga & Penjualan | `unit_price_usd`, `discount_pct`, `units_sold`, `discounted_price_usd`, `revenue_usd` |
| 💱 Mata Uang | `currency`, `fx_rate_to_usd`, `revenue_local_currency` |
| 🛒 Transaksi | `sales_channel`, `payment_method` |
| 👤 Pelanggan | `customer_segment`, `customer_age_group`, `previous_device_os`, `customer_rating`, `return_status` |

---

## Pipeline Analisis

```
Data Understanding  →  Data Cleaning  →  EDA  →  Business Insights
```

---

## Data Understanding

Eksplorasi awal dilakukan untuk memahami struktur, karakteristik, dan kualitas data.

### Temuan Awal

- **Tipe data:** object (string), integer, dan float
- **Duplikasi:** tidak ditemukan data duplikat
- **Missing values** ditemukan pada 3 kolom:

| Kolom | Jumlah Null |
|---|---|
| `storage` | 4.804 |
| `previous_device_os` | 8.056 |
| `customer_rating` | 3.360 |

### Indikasi Outlier

Beberapa variabel menunjukkan perbedaan signifikan antara nilai maksimum dan median:

| Variabel | Nilai Maks | Keterangan |
|---|---|---|
| `unit_price_usd` | $7.551 | Produk high-end Mac Pro |
| `revenue_usd` | $59.529 | Transaksi multi-unit Mac Pro |
| `fx_rate_to_usd` | 24.500 | Kurs Dong Vietnam (valid) |
| `revenue_local_currency` | 507.517.500 | Efek kurs VND × transaksi premium |

---

## Data Cleaning

### 1. Missing Values — `storage`
**Solusi:** Diisi dengan `"Not Applicable"`

Produk seperti AirPods, Magic Keyboard, dan aksesori memang tidak memiliki atribut storage yang relevan. Nilai null bukan error, melainkan mencerminkan karakteristik produk.

### 2. Missing Values — `previous_device_os`
**Solusi:** Kolom dihapus

Proporsi missing values (8.056) terlalu tinggi untuk dilakukan imputasi secara representatif. Menghapus kolom ini mengurangi noise tanpa mengorbankan analisis utama.

### 3. Missing Values — `customer_rating`
**Solusi:** Diisi dengan nilai **median**

Jumlah null masih tergolong dapat dikelola. Median dipilih karena lebih stabil terhadap outlier dibanding mean.

### 4. Outlier
Seluruh nilai ekstrem pada `unit_price_usd`, `revenue_usd`, `fx_rate_to_usd`, dan `revenue_local_currency` **dipertahankan** setelah divalidasi — semua terbukti merupakan transaksi premium yang valid, bukan kesalahan data.

---

## Exploratory Data Analysis

EDA dilakukan melalui **10 pertanyaan investigatif** untuk memastikan setiap analisis memiliki tujuan bisnis yang jelas.

---

## Key Insights

### 1. Produk terlaris ≠ revenue tertinggi
- **Terlaris:** Apple Watch SE (2nd Gen) — 664 unit
- **Revenue tertinggi:** Mac Pro (M2 Ultra) — ~$298 juta USD

> 💡 Produk premium berkontribusi lebih besar terhadap revenue meskipun volume penjualannya lebih rendah.

---

### 2. Negara dengan kontribusi revenue terbesar

| Peringkat | Negara | Revenue (USD) |
|---|---|---|
| 1 | Hong Kong | ~$42 juta |
| 2 | Canada | ~$39 juta |
| 3 | Germany, Thailand, Mexico | ~$38 juta |
| 4 | Japan | ~$37 juta |
| 5 | New Zealand, Turkey | ~$36 juta |

> 💡 Distribusi pasar global cukup merata — negara berkembang seperti Thailand dan Mexico mampu bersaing dengan negara maju.

---

### 3. Harga tidak memengaruhi quantity pembelian
Korelasi antara `unit_price_usd` dan `units_sold` hanya **−0.003** — hampir tidak ada hubungan. Konsumen Apple tidak sensitif terhadap harga; loyalitas brand dan kebutuhan pengguna lebih berpengaruh.

---

### 4. Preferensi storage pelanggan

| Peringkat | Storage | Unit Terjual |
|---|---|---|
| 1 | 64 GB | 1.947 |
| 2 | 256 GB | 1.888 |
| 3 | 512 GB | 1.861 |
| 4 | 1 TB | 1.849 |
| 5 | 128 GB | 1.751 |

> 💡 Preferensi storage cukup beragam — pelanggan tidak hanya memilih kapasitas terkecil untuk menghemat biaya.

---

### 5. Revenue tinggi berasal dari transaksi bernilai besar
Mac Pro (~$3.7M revenue) hanya memiliki 275 transaksi dibanding Apple Watch SE dengan 312 transaksi. **Nilai per transaksi lebih menentukan revenue daripada frekuensi pembelian.**

---

### 6. Customer rating konsisten di semua produk
Korelasi antara rating dan revenue hanya **0.001**. Rata-rata rating semua kategori berada di sekitar **4.0/5.0** — Apple menjaga kepuasan pelanggan yang stabil di seluruh lini produk.

---

### 7. Warna produk favorit

| Peringkat | Warna | Unit Terjual |
|---|---|---|
| 1 | Silver | 3.420 |
| 2 | Space Gray | 2.503 |
| 3 | Starlight | 2.416 |

> 💡 Konsumen Apple cenderung menyukai warna netral dan elegan — mencerminkan preferensi desain yang profesional.

---

### 8. Pola pembelian antarnegara
iPhone mendominasi preferensi di hampir seluruh negara. **Pengecualian:** Canada justru lebih banyak membeli Accessories — mengindikasikan adopsi ekosistem Apple yang sangat matang.

---

### 9. Outlier revenue adalah transaksi premium yang valid
Semua nilai ekstrem terverifikasi valid:
- Harga tinggi → produk Mac Pro (M2 Ultra)
- FX rate tinggi → kurs Dong Vietnam (24.500 VND/USD)
- Revenue lokal tinggi → kombinasi kurs VND × pembelian Mac Pro multi-unit

---

### 10. Faktor paling berpengaruh terhadap revenue

| Faktor | Korelasi dengan Revenue |
|---|---|
| `unit_price_usd` | **0.755** ✅ paling kuat |
| `units_sold` | 0.384 |
| `revenue_local_currency` | 0.139 |

> 💡 **Harga produk adalah faktor utama penentu revenue.** Strategi penjualan produk premium berdampak lebih besar terhadap pendapatan dibanding hanya meningkatkan volume penjualan.

---

## Kesimpulan

Analisis ini menunjukkan bahwa:

1. **Strategi premium terbukti efektif** — produk high-end seperti Mac Pro memberikan kontribusi revenue yang tidak proporsional dibanding volumenya
2. **Konsumen Apple tidak price-sensitive** — loyalitas brand sangat kuat
3. **Pasar global terdistribusi merata** — Hong Kong, Canada, dan beberapa negara berkembang menjadi kontributor terbesar
4. **Kualitas data terjaga** — seluruh outlier terbukti valid setelah divalidasi secara bisnis

---

*Dataset: Apple Global Product Sales Dataset (2022–2024)*
