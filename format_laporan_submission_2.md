# Laporan Proyek Machine Learning - Mohammad Nurdin Prastya Hermansah

## Project Overview

Dalam era digital saat ini, platform streaming musik seperti Spotify menghadapi tantangan untuk menyajikan pengalaman yang personal dan relevan bagi setiap penggunanya. Dengan jutaan lagu yang tersedia, pengguna dapat merasa kewalahan dalam memilih musik yang sesuai dengan selera mereka. Oleh karena itu, sistem rekomendasi berbasisi content base filter ini menjadi fitur krusial yang membantu pengguna menemukan musik baru yang kemungkinan besar akan mereka sukai.

Proyek ini bertujuan untuk membangun sistem rekomendasi musik berbasis konten (Content-Based Filtering) yang dapat merekomendasikan lagu-lagu serupa berdasarkan fitur-fitur audio seperti energi, valensi, danceability, dan tempo. Sistem ini berfokus pada karakteristik intrinsik dari lagu itu sendiri, bukan pada interaksi antar pengguna. Pendekatan ini relevan khususnya dalam situasi cold-start, di mana data interaksi pengguna belum tersedia atau masih terbatas.

Sistem rekomendasi memiliki peran penting dalam meningkatkan user engagement dan retensi pengguna di platform digital. Berdasarkan laporan dari McKinsey, sistem rekomendasi yang efektif dapat meningkatkan penjualan hingga 20% dan meningkatkan kepuasan pelanggan melalui pengalaman yang lebih personal. Spotify sendiri menggunakan kombinasi sistem rekomendasi, termasuk collaborative filtering dan content-based filtering, untuk menghasilkan fitur seperti Discover Weekly dan Daily Mix. Dengan mengembangkan sistem rekomendasi berbasis konten menggunakan data publik dari Spotify, proyek ini tidak hanya melatih kemampuan teknis dalam analisis data dan machine learning, tetapi juga memberikan pemahaman praktis mengenai cara kerja sistem rekomendasi dalam industri teknologi saat ini.

## Business Understanding

Pada bagian ini, Anda perlu menjelaskan proses klarifikasi masalah.

Bagian laporan ini mencakup:

### Problem Statements

Menjelaskan pernyataan masalah:
- Pernyataan Masalah 1
- Pernyataan Masalah 2
- Pernyataan Masalah n

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Jawaban pernyataan masalah 1
- Jawaban pernyataan masalah 2
- Jawaban pernyataan masalah n

Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Menambahkan bagian “Solution Approach” yang menguraikan cara untuk meraih goals. Bagian ini dibuat dengan ketentuan sebagai berikut: 

    ### Solution statements
    - Mengajukan 2 atau lebih solution approach (algoritma atau pendekatan sistem rekomendasi).

## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai jumlah data, kondisi data, dan informasi mengenai data yang digunakan. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
