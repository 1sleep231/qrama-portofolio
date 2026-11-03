# Data Catalog for Gold Layer

## 📌 Overview
Gold Layer merupakan representasi data pada level bisnis yang telah terstruktur untuk mendukung kebutuhan analisis dan pelaporan. Layer ini terdiri dari **tabel dimensi (dimension tables)** dan **tabel fakta (fact tables)** yang digunakan untuk mengukur metrik bisnis secara spesifik.

---

## 🧩 1. gold.dim_customers

### 🎯 Tujuan
Menyimpan informasi pelanggan yang telah diperkaya dengan data demografis dan geografis.

### 🧾 Struktur Kolom

| Nama Kolom       | Tipe Data     | Deskripsi                                                                 |
|------------------|--------------|--------------------------------------------------------------------------|
| customer_key     | INT          | Primary key (surrogate key) unik untuk setiap data pelanggan.            |
| customer_id      | INT          | Identitas numerik unik untuk setiap pelanggan.                           |
| customer_number  | NVARCHAR(50) | Kode alfanumerik pelanggan untuk keperluan tracking.                     |
| first_name       | NVARCHAR(50) | Nama depan pelanggan.                                                    |
| last_name        | NVARCHAR(50) | Nama belakang pelanggan.                                                 |
| country          | NVARCHAR(50) | Negara tempat tinggal pelanggan.                                         |
| marital_status   | NVARCHAR(50) | Status pernikahan pelanggan (misalnya: Married, Single).                 |
| gender           | NVARCHAR(50) | Jenis kelamin pelanggan.                                                 |
| birthdate        | DATE         | Tanggal lahir pelanggan (format YYYY-MM-DD).                             |
| create_date      | DATE         | Tanggal pembuatan data pelanggan dalam sistem.                           |

---

## 🧩 2. gold.dim_products

### 🎯 Tujuan
Menyediakan informasi terkait produk beserta atribut-atributnya.

### 🧾 Struktur Kolom

| Nama Kolom          | Tipe Data     | Deskripsi                                                                 |
|---------------------|--------------|--------------------------------------------------------------------------|
| product_key         | INT          | Primary key (surrogate key) unik untuk setiap produk.                    |
| product_id          | INT          | Identitas unik produk dalam sistem.                                      |
| product_number      | NVARCHAR(50) | Kode alfanumerik produk untuk identifikasi dan inventaris.               |
| product_name        | NVARCHAR(50) | Nama produk yang bersifat deskriptif (jenis, warna, ukuran).             |
| category_id         | NVARCHAR(50) | ID kategori produk.                                                      |
| category            | NVARCHAR(50) | Kategori utama produk (misalnya: Bikes, Components).                     |
| subcategory         | NVARCHAR(50) | Subkategori yang lebih spesifik dari produk.                             |
| maintenance_required| NVARCHAR(50) | Menunjukkan apakah produk membutuhkan perawatan (Yes/No).                |
| cost                | INT          | Harga dasar atau biaya produk.                                           |
| product_line        | NVARCHAR(50) | Lini produk (misalnya: Road, Mountain).                                  |
| start_date          | DATE         | Tanggal produk mulai tersedia.                                           |

---

## 🧩 3. gold.fact_sales

### 🎯 Tujuan
Menyimpan data transaksi penjualan yang digunakan untuk analisis bisnis.

### 🧾 Struktur Kolom

| Nama Kolom     | Tipe Data     | Deskripsi                                                                 |
|----------------|--------------|--------------------------------------------------------------------------|
| order_number   | NVARCHAR(50) | Kode unik untuk setiap transaksi penjualan.                              |
| product_key    | INT          | Foreign key yang terhubung ke tabel produk.                              |
| customer_key   | INT          | Foreign key yang terhubung ke tabel pelanggan.                           |
| order_date     | DATE         | Tanggal pemesanan dilakukan.                                             |
| shipping_date  | DATE         | Tanggal pengiriman pesanan.                                              |
| due_date       | DATE         | Tanggal jatuh tempo pembayaran.                                          |
| sales_amount   | INT          | Total nilai penjualan untuk item tersebut.                               |
| quantity       | INT          | Jumlah unit produk yang dibeli.                                          |
| price          | INT          | Harga per unit produk.                                                   |

---

## 🧠 Insight Struktur Data

Gold Layer ini dirancang untuk:
- Mendukung analisis berbasis bisnis (business intelligence)
- Mempermudah pembuatan dashboard dan reporting
- Mengintegrasikan data dimensi dan transaksi secara efisien

Struktur ini mengikuti konsep **star schema**, di mana:
- `fact_sales` sebagai pusat (fact table)
- `dim_customers` dan `dim_products` sebagai tabel dimensi

---

## ⭐ Highlight

> Struktur Gold Layer ini menunjukkan implementasi data warehouse yang siap digunakan untuk analisis lanjutan dan pengambilan keputusan berbasis data.