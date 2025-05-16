# Laporan Proyek Machine Learning - Mohammad Nurdin Prastya Hermansah

## Project Overview

![image](https://github.com/user-attachments/assets/1631de35-9008-447e-b0f1-71ba4e7e41d1)

Dalam era digital saat ini, platform streaming musik seperti Spotify menghadapi tantangan untuk menyajikan pengalaman yang personal dan relevan bagi setiap penggunanya. Dengan jutaan lagu yang tersedia, pengguna dapat merasa kewalahan dalam memilih musik yang sesuai dengan selera mereka. Oleh karena itu, sistem rekomendasi berbasisi content base filter ini menjadi fitur krusial yang membantu pengguna menemukan musik baru yang kemungkinan besar akan mereka sukai.

Proyek ini bertujuan untuk membangun sistem rekomendasi musik berbasis konten (Content-Based Filtering) yang dapat merekomendasikan lagu-lagu serupa berdasarkan fitur-fitur audio seperti energi, valensi, danceability, dan tempo. Sistem ini berfokus pada karakteristik intrinsik dari lagu itu sendiri, bukan pada interaksi antar pengguna. Pendekatan ini relevan khususnya dalam situasi cold-start, di mana data interaksi pengguna belum tersedia atau masih terbatas.

Sistem rekomendasi memiliki peran penting dalam meningkatkan user engagement dan retensi pengguna di platform digital. Berdasarkan laporan dari McKinsey, sistem rekomendasi yang efektif dapat meningkatkan penjualan hingga 20% dan meningkatkan kepuasan pelanggan melalui pengalaman yang lebih personal. Spotify sendiri menggunakan kombinasi sistem rekomendasi, termasuk collaborative filtering dan content-based filtering, untuk menghasilkan fitur seperti Discover Weekly dan Daily Mix. Dengan mengembangkan sistem rekomendasi berbasis konten menggunakan data publik dari Spotify, proyek ini tidak hanya melatih kemampuan teknis dalam analisis data dan machine learning, tetapi juga memberikan pemahaman praktis mengenai cara kerja sistem rekomendasi dalam industri teknologi saat ini.

<img width="821" alt="image" src="https://github.com/user-attachments/assets/0807bf47-eb7f-4145-918b-a8581b53cbdf" />

Proses dimulai dari Business Understanding, yaitu tahapan memahami masalah bisnis dan kemudian mrancang solusi analitik berdasarkan data untuk menyelesaikan permasalahan tersebut. Tahapan yang dijelaskan pada tahapan ini meliputi problem statement, goals, dan solution approach. Setelah memahami masalah dan menentukan solusinya, tahapan berlanjut pada Data Understanding dengan melihat infromasi data dan menentukan kualitasnya. Pemahaman data sangat penting untuk menghindari masalah yang tidak terduga pada fase berikutnya, yaitu Data Preparation. Data preparation di proyek ini adalah melakukan cleaning data yang hilang dan meng-encode data sehingga dapat diproses model, lalu pada akhirnya membagi data menjadi training dan test sebelum melakukan pemodelan. Pada tahap pemodelan dan evaluasi, dilakukan proses trainng dan melihat ukuran performa dari model untuk menentukan apakah model tersebut baik atau kurang.

----------------------------------------------------

## Business Understanding

### Problem Statements
Dalam ekosistem platform streaming musik seperti Spotify, pengguna seringkali mengalami kesulitan dalam menemukan lagu baru yang sesuai dengan selera mereka. Dengan jumlah lagu yang sangat besar dan beragam, pengguna membutuhkan sistem yang mampu menyaring dan merekomendasikan konten musik secara personal. Tanpa sistem rekomendasi yang efektif, pengalaman pengguna akan menjadi kurang optimal, yang pada akhirnya dapat berdampak pada retensi pengguna.

Masalah utama yang ingin diselesaikan dalam proyek ini adalah:
1. Bagaimana membangun sistem yang mampu merekomendasikan lagu-lagu yang relevan bagi pengguna berdasarkan lagu yang mereka sukai?
2. Bagaimana mengukur seberapa baik sistem rekomendasi yang dibangun dalam menyajikan hasil yang relevan dan akurat?

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
