# Laporan Proyek Machine Learning System Recomendation Music Spotify - Mohammad Nurdin Prastya Hermansah

## Project Overview

![image](https://github.com/user-attachments/assets/1631de35-9008-447e-b0f1-71ba4e7e41d1)

Dalam era digital saat ini, platform streaming musik seperti Spotify menghadapi tantangan untuk menyajikan pengalaman yang personal dan relevan bagi setiap penggunanya. Dengan jutaan lagu yang tersedia, pengguna dapat merasa kewalahan dalam memilih musik yang sesuai dengan selera mereka. Oleh karena itu, sistem rekomendasi berbasisi content base filter ini menjadi fitur krusial yang membantu pengguna menemukan musik baru yang kemungkinan besar akan mereka sukai.

Proyek ini bertujuan untuk membangun sistem rekomendasi musik berbasis konten (Content-Based Filtering) yang dapat merekomendasikan lagu-lagu serupa berdasarkan fitur-fitur audio seperti track_id, track_name, track_artist, playlist_genre, playlist_subgenre, duration_label, energy_level dan danceability_level. Sistem ini berfokus pada karakteristik intrinsik dari lagu itu sendiri, bukan pada interaksi antar pengguna. Pendekatan ini relevan khususnya dalam situasi cold-start, di mana data interaksi pengguna belum tersedia atau masih terbatas.

Sistem rekomendasi memiliki peran penting dalam meningkatkan user engagement dan retensi pengguna di platform digital. Berdasarkan laporan dari McKinsey, sistem rekomendasi yang efektif dapat meningkatkan penjualan hingga 20% dan meningkatkan kepuasan pelanggan melalui pengalaman yang lebih personal. Spotify sendiri menggunakan kombinasi sistem rekomendasi, termasuk collaborative filtering dan content-based filtering, untuk menghasilkan fitur seperti Discover Weekly dan Daily Mix. Dengan mengembangkan sistem rekomendasi berbasis konten menggunakan data publik dari Spotify, proyek ini tidak hanya melatih kemampuan teknis dalam analisis data dan machine learning, tetapi juga memberikan pemahaman praktis mengenai cara kerja sistem rekomendasi dalam industri teknologi saat ini.

<img width="821" alt="image" src="https://github.com/user-attachments/assets/0807bf47-eb7f-4145-918b-a8581b53cbdf" />

**Gambar 1.** Alur Proyek Sistem Rekomendasi

Proses dimulai dari Business Understanding, yaitu tahapan memahami masalah bisnis dan kemudian mrancang solusi analitik berdasarkan data untuk menyelesaikan permasalahan tersebut. Tahapan yang dijelaskan pada tahapan ini meliputi problem statement, goals, dan solution approach. Setelah memahami masalah dan menentukan solusinya, tahapan berlanjut pada Data Understanding dengan melihat infromasi data dan menentukan kualitasnya. Pemahaman data sangat penting untuk menghindari masalah yang tidak terduga pada fase berikutnya, yaitu Data Preparation. Data preparation di proyek ini adalah melakukan cleaning data yang hilang dan meng-encode data sehingga dapat diproses model, lalu pada akhirnya membagi data menjadi training dan test sebelum melakukan pemodelan. Pada tahap pemodelan dan evaluasi, dilakukan proses trainng dan melihat ukuran performa dari model untuk menentukan apakah model tersebut baik atau kurang.

----------------------------------------------------

## Business Understanding

### Problem Statements
Dalam ekosistem platform streaming musik seperti Spotify, pengguna seringkali mengalami kesulitan dalam menemukan lagu baru yang sesuai dengan selera mereka. Dengan jumlah lagu yang sangat besar dan beragam, pengguna membutuhkan sistem yang mampu menyaring dan merekomendasikan konten musik secara personal. Tanpa sistem rekomendasi yang efektif, pengalaman pengguna akan menjadi kurang optimal, yang pada akhirnya dapat berdampak pada retensi pengguna.

Masalah utama yang ingin diselesaikan dalam proyek ini adalah:
1. Bagaimana membangun sistem yang mampu merekomendasikan lagu-lagu yang relevan bagi pengguna berdasarkan lagu yang mereka sukai?
2. Bagaimana mengukur seberapa baik sistem rekomendasi yang dibangun dalam menyajikan hasil yang relevan dan akurat?

### Goals
Tujuan dari proyek ini adalah:
1. Mengembangkan sistem rekomendasi musik yang mampu memberikan daftar rekomendasi lagu berdasarkan input lagu tertentu.
2. Mengimplementasikan pendekatan Content-Based Filtering untuk menghasilkan Top-N recommendation yang akurat.
3. Membandingkan pendekatan Content-Based dengan pendekatan alternatif seperti Collaborative Filtering, serta mengevaluasi kelebihan dan kekurangannya dalam konteks data yang tersedia.

### Solution statements
Untuk mencapai tujuan tersebut dipilih satu pendekatan utama dalam pengembangan sistem rekomendasi musik di spotify yaitu:
1. Content-Based Filtering
Pendekatan ini merekomendasikan lagu-lagu berdasarkan kemiripan fitur kontennya seperti track_id, track_name, track_artist, playlist_genre, playlist_subgenre, duration_label, energy_level dan danceability_level. Sistem ini bekerja dengan menghitung kemiripan antar lagu menggunakan metode seperti cosine similarity. Misalnya, jika pengguna menyukai lagu dengan genre pop, sistem akan menyarankan lagu lain dengan karakteristik yang serupa yaitu pop musik.
2. Collaborative Filtering
Pendekatan ini menggunakan pola interaksi pengguna (seperti user rating atau history mendengarkan) untuk merekomendasikan lagu. Sistem ini menyarankan lagu yang disukai oleh pengguna lain yang memiliki preferensi serupa.

Dalam proyek ini, pendekatan Content-Based Filtering dipilih dan diimplementasikan terlebih dahulu karena ketersediaan fitur konten lagu yang kaya dan ketiadaan data interaksi pengguna.

## Data Understanding
Sumber dataset yang digunakan dalam proyek ini berasal dari repositori publik milik TidyTuesday, Untuk melihat atau menggunakan daatset ini silahkan kunjungi link ini ( https://github.com/rfordatascience/tidytuesday/blob/master/data/2020/2020-01-21/spotify_songs.csv ) atau bisa juga langsung copy dan gunakan pada proyek dengan kode seperti dibawah ini.

<img width="947" alt="image" src="https://github.com/user-attachments/assets/2ed8551b-c83f-4824-9c84-3ac5f77df1e0" />


Dataset ini berisi data lagu-lagu dari Spotify Top 2000 berdasarkan tangga lagu Spotify Charts dari tahun 2017 hingga 2019, dengan informasi berbagai fitur audio yang diperoleh melalui Spotify Web API.

Informasi Umum Dataset
Jumlah baris (lagu): 32.833 lagu

Jumlah kolom (fitur): 23 fitur

Dataset ini sudah cukup bersih dan tidak memiliki banyak nilai kosong. Namun, tetap dilakukan pemeriksaan dan eksplorasi untuk memastikan kualitas data.

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
