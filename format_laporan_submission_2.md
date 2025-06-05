# Laporan Proyek Machine Learning System Recomendation Music Spotify Dengan Colaboratif Content Filter - Mohammad Nurdin Prastya Hermansah

## Project Overview
<div align="center">
<img src="https://github.com/user-attachments/assets/1631de35-9008-447e-b0f1-71ba4e7e41d1" alt="Gambar 1: Alur Proyek Sistem Rekomendasi" width="800"/>
<br/>
<strong>Gambar 1.</strong> Aplikasi Spotify
</div>

Dalam era digital saat ini, platform streaming musik seperti Spotify menghadapi tantangan untuk menyajikan pengalaman yang personal dan relevan bagi setiap penggunanya. Dengan jutaan lagu yang tersedia, pengguna dapat merasa kewalahan dalam memilih musik yang sesuai dengan selera mereka. Oleh karena itu, sistem rekomendasi berbasisi content base filter ini menjadi fitur krusial yang membantu pengguna menemukan musik baru yang kemungkinan besar akan mereka sukai.

Proyek ini bertujuan untuk membangun sistem rekomendasi musik berbasis konten (Content-Based Filtering) yang dapat merekomendasikan lagu-lagu serupa berdasarkan fitur-fitur audio seperti track_id, track_name, track_artist, playlist_genre, playlist_subgenre, duration_label, energy_level dan danceability_level. Sistem ini berfokus pada karakteristik intrinsik dari lagu itu sendiri, bukan pada interaksi antar pengguna. Pendekatan ini relevan khususnya dalam situasi cold-start, di mana data interaksi pengguna belum tersedia atau masih terbatas.

Sistem rekomendasi memiliki peran penting dalam meningkatkan user engagement dan retensi pengguna di platform digital. Berdasarkan laporan dari McKinsey, sistem rekomendasi yang efektif dapat meningkatkan penjualan hingga 20% dan meningkatkan kepuasan pelanggan melalui pengalaman yang lebih personal. Spotify sendiri menggunakan kombinasi sistem rekomendasi, termasuk collaborative filtering dan content-based filtering, untuk menghasilkan fitur seperti Discover Weekly dan Daily Mix. Dengan mengembangkan sistem rekomendasi berbasis konten menggunakan data publik dari Spotify, proyek ini tidak hanya melatih kemampuan teknis dalam analisis data dan machine learning, tetapi juga memberikan pemahaman praktis mengenai cara kerja sistem rekomendasi dalam industri teknologi saat ini.

<div align="center">
<img width="804" alt="Alur Proyek Sistem Rekomendasi" src="https://github.com/user-attachments/assets/d3432142-127b-4e02-9296-6228fcfb7e3c" />
<br/>
<strong>Gambar 2.</strong> Alur Proyek Sistem Rekomendasi
</div>

Proses dimulai dari Business Understanding, yaitu tahapan memahami masalah bisnis dan kemudian mrancang solusi analitik berdasarkan data untuk menyelesaikan permasalahan tersebut. Tahapan yang dijelaskan pada tahapan ini meliputi problem statement, goals, dan solution approach. Setelah memahami masalah dan menentukan solusinya, tahapan berlanjut pada Data Understanding dengan melihat infromasi data dan menentukan kualitasnya. Pemahaman data sangat penting untuk menghindari masalah yang tidak terduga pada fase berikutnya, yaitu Data Preparation. Data preparation di proyek ini adalah melakukan cleaning data yang hilang dan meng-encode data sehingga dapat diproses model, lalu pada akhirnya membagi data menjadi training dan test sebelum melakukan pemodelan. Pada tahap pemodelan dan evaluasi, dilakukan proses trainng dan melihat ukuran performa dari model untuk menentukan apakah model tersebut baik atau kurang.


----------------------------------------------------


## Business Understanding

### Problem Statements
Dalam ekosistem platform streaming musik seperti Spotify, pengguna seringkali mengalami kesulitan dalam menemukan lagu baru yang sesuai dengan selera mereka. Dengan jumlah lagu yang sangat besar dan beragam, pengguna membutuhkan sistem yang mampu menyaring dan merekomendasikan konten musik secara personal. Tanpa sistem rekomendasi yang efektif, pengalaman pengguna akan menjadi kurang optimal, yang pada akhirnya dapat berdampak pada retensi pengguna.

Masalah utama yang ingin diselesaikan dalam proyek ini adalah:
1. Bagaimana membangun sistem yang mampu merekomendasikan lagu-lagu yang relevan bagi pengguna berdasarkan lagu yang mereka sukai?
2. Bagaimana memahami struktur dan karakteristik dataset yang tersedia (playlist, lagu, genre, durasi, popularitas, dll.) untuk mendukung pengembangan sistem rekomendasi?
3. Bagaimana cara untuk mendapatkan rekomendasi lagu Top-N recomendation?

### Goals
Tujuan dari proyek ini adalah:
1. Mengembangkan sistem rekomendasi musik yang mampu memberikan daftar rekomendasi lagu berdasarkan input lagu tertentu seperti id musik, genre dan keyword nama lagu.
2. Melakukan eksplorasi dan analisis data untuk memahami karakteristik playlist, lagu, genre, artis, dan fitur lain yang mendukung pembangunan sistem rekomendasi.
3. Mengimplementasikan pendekatan Content-Based Filtering untuk menghasilkan Top-N recommendation yang akurat.

### Solution statements
Untuk mencapai tujuan tersebut dipilih satu pendekatan utama dalam pengembangan sistem rekomendasi musik di spotify yaitu:
1. Content-Based Filtering
Pendekatan ini merekomendasikan lagu-lagu berdasarkan kemiripan fitur kontennya seperti track_id, track_name, track_artist, playlist_genre, playlist_subgenre, duration_label, energy_level dan danceability_level. Sistem ini bekerja dengan menghitung kemiripan antar lagu menggunakan metode seperti cosine similarity. Misalnya, jika pengguna menyukai lagu dengan genre pop, sistem akan menyarankan lagu lain dengan karakteristik yang serupa yaitu pop musik.
2. Collaborative Filtering
Pendekatan ini menggunakan pola interaksi pengguna (seperti user rating atau history mendengarkan) untuk merekomendasikan lagu. Sistem ini menyarankan lagu yang disukai oleh pengguna lain yang memiliki preferensi serupa.

Dalam proyek ini, pendekatan Content-Based Filtering dipilih dan diimplementasikan terlebih dahulu karena ketersediaan fitur konten lagu yang kaya dan ketiadaan data interaksi pengguna.


----------------------------------------------------


## Data Understanding
### Sumber Data
Sumber dataset yang digunakan dalam proyek ini berasal dari repositori publik milik TidyTuesday, Untuk melihat atau menggunakan daatset ini silahkan kunjungi link ini ( https://github.com/rfordatascience/tidytuesday/blob/master/data/2020/2020-01-21/spotify_songs.csv ) atau bisa juga langsung copy dan gunakan pada proyek dengan kode seperti dibawah ini.
```
# dwonload data
url = "https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2020/2020-01-21/spotify_songs.csv"
data = pd.read_csv(url)
```
### Informasi Umum Dataset
Dataset ini berisi data lagu-lagu dari Spotify Top 2000 berdasarkan tangga lagu Spotify Charts dari tahun 2017 hingga 2019, dengan informasi berbagai fitur audio yang diperoleh melalui Spotify Web API.
Informasi Umum Dataset
1. Jumlah baris (lagu): 32.833 lagu
2. Jumlah kolom (fitur): 23 fitur

Berikut adalah tabel berisi 23 fitur dari dataset spotify_songs.csv lengkap dengan deskripsi singkat masing-masing fitur:
| No. | Nama Fitur                 | Tipe Data | Deskripsi                                                          |
| --- | -------------------------- | --------- | ------------------------------------------------------------------ |
| 1   | `track_id`                 | object    | ID unik untuk setiap lagu (track) di Spotify.                      |
| 2   | `track_name`               | object    | Nama lagu.                                                         |
| 3   | `track_artist`             | object    | Nama artis yang membawakan lagu.                                   |
| 4   | `track_popularity`         | int64     | Skor popularitas lagu di Spotify (0-100).                          |
| 5   | `track_album_id`           | object    | ID unik dari album tempat lagu berada.                             |
| 6   | `track_album_name`         | object    | Nama album tempat lagu dirilis.                                    |
| 7   | `track_album_release_date` | object    | Tanggal rilis album.                                               |
| 8   | `playlist_name`            | object    | Nama playlist tempat lagu berada.                                  |
| 9   | `playlist_id`              | object    | ID unik dari playlist.                                             |
| 10  | `playlist_genre`           | object    | Genre utama dari playlist.                                         |
| 11  | `playlist_subgenre`        | object    | Subgenre atau genre yang lebih spesifik dari playlist.             |
| 12  | `danceability`             | float64   | Seberapa cocok lagu untuk menari (0-1).                            |
| 13  | `energy`                   | float64   | Intensitas dan aktivitas lagu (0-1).                               |
| 14  | `key`                      | int64     | Nada dasar lagu, direpresentasikan dalam bentuk integer (0–11).    |
| 15  | `loudness`                 | float64   | Tingkat kekerasan suara lagu dalam desibel (dB).                   |
| 16  | `mode`                     | int64     | Modus musik: mayor (1) atau minor (0).                             |
| 17  | `speechiness`              | float64   | Ukuran seberapa banyak elemen lirik atau suara manusia dalam lagu. |
| 18  | `acousticness`             | float64   | Tingkat keakustikan lagu (0-1).                                    |
| 19  | `instrumentalness`         | float64   | Kemungkinan lagu tidak mengandung vokal (0-1).                     |
| 20  | `liveness`                 | float64   | Indikasi apakah lagu direkam secara live (0-1).                    |
| 21  | `valence`                  | float64   | Positif atau cerianya lagu secara musikal (0-1).                   |
| 22  | `tempo`                    | float64   | Kecepatan lagu dalam beat per minute (BPM).                        |
| 23  | `duration_ms`              | int64     | Durasi lagu dalam milidetik.                                       |

   
Berikut adalah versi dalam bentuk tabel untuk bagian "kolom yang digunakan" dalam proyek ini, lengkap dengan deskripsi singkat masing-masing kolom:
| No. | Nama Kolom           | Deskripsi                                                                 |
| --- | -------------------- | ------------------------------------------------------------------------- |
| 1   | `track_id`           | ID unik untuk tiap lagu.                                                  |
| 2   | `track_name`         | Nama lagu.                                                                |
| 3   | `track_artist`       | Nama artis atau penyanyi lagu.                                            |
| 4   | `playlist_genre`     | Genre utama dari playlist tempat lagu berada.                             |
| 5   | `playlist_subgenre`  | Subgenre yang lebih spesifik dari playlist.                               |
| 6   | `duration_label`     | Kategori durasi lagu (misalnya: pendek, sedang, panjang).                 |
| 7   | `energy_level`       | Kategori tingkat energi lagu (dari rendah hingga tinggi).                 |
| 8   | `danceability_level` | Kategori tingkat kemudahan lagu untuk didansa.                            |
| 9   | `combined_features`  | Gabungan berbagai fitur numerik untuk keperluan analisis dan rekomendasi. |

Dataset ini sudah cukup bersih dan tidak memiliki banyak nilai kosong. Namun, tetap dilakukan pemeriksaan dan eksplorasi untuk memastikan kualitas data.

### Eksplorasi Data & Visualisasi Data
Beberapa langkah exploratory data analysis (EDA) dilakukan untuk memahami distribusi dan hubungan antar fitur dan dibawah ini adalah resmue dari beberapa tahapan yang sudah dilakukan. kode dibawah ini adalah kode untuk membuat resum pada analisis eda yang sudah dilakukan, disarankan untuk melihat code keseluruhan pada file ipynb agar tidak terjadi eror. Berikut ini kodenya:
```python
# Ringkasan jumlah entitas
summary_df = pd.DataFrame ({
    "Kategori": [
        "Total playlist id",
        "Total Lagu Unik", 
        "Track paling populer",
        "Track paling jarang",
        "Total nama lagu",
        "Lagu Terpopuler (Spotify)",
        "Total Playlist Unik",
        "Jumlah main genre",
        "Jumlah sub genre",
        "Genre Terpopuler", 
        "Subgenre Terpopuler",
        "Artis dengan Lagu Paling Banyak Didengar",
        "Track dengan Durasi Terlama",
        "Track dengan Durasi Terpendek"
    ],
    "Nilai": [
        cf_df['playlist_id'].nunique(),
        cf_df['track_id'].nunique(),
        cf_df['track_id'].value_counts().idxmax(),
        cf_df['track_id'].value_counts().idxmin(),
        cbf_df['track_name'].nunique(),
        top_spotify_info,
        cf_df['playlist_id'].nunique(),
        cbf_df['playlist_genre'].nunique(),
        cbf_df['playlist_subgenre'].nunique(),
        cbf_df['playlist_genre'].value_counts().idxmax(),
        cbf_df['playlist_subgenre'].value_counts().idxmax(),
        most_popular_artist,
        longest_track_summary,
        shortest_track_summary
    ]
})


# Tampilkan ringkasan EDA
print("=== Ringkasan EDA ===")
display(summary_df)
```
Hasil dari kode diatas akan menampilkan statistik deskriptif seperti dibawah ini:
| Index | Kategori                             | Nilai                                                   |
|-------|--------------------------------------|----------------------------------------------------------|
| 0     | Total playlist id                    | 425                                                      |
| 1     | Total Lagu Unik                      | 1487                                                     |
| 2     | Track paling populer                 | 7LzouaWGFCy4tkXDOOnEyM                                   |
| 3     | Track paling jarang                  | 5fCwwY9VFcpQr1JOKsHmPX                                   |
| 4     | Total nama lagu                      | 1459                                                     |
| 5     | Lagu Terpopuler (Spotify)           | ROXANNE - Arizona Zervas (99)                            |
| 6     | Total Playlist Unik                  | 425                                                      |
| 7     | Jumlah main genre                    | 6                                                        |
| 8     | Jumlah sub genre                     | 24                                                       |
| 9     | Genre Terpopuler                     | rap                                                      |
| 10    | Subgenre Terpopuler                  | indie poptimism                                          |
| 11    | Artis dengan Lagu Paling Banyak Didengar | The Chainsmokers                                   |
| 12    | Lagu dengan Durasi Terlama          | Shake Your Body (Down to the Ground) - The Jacksons (7:59) |
| 13    | Lagu dengan Durasi Terpendek        | Canción del encantamiento oleh Carmen López (0:54)       |


----------------------------------------------------


## Data Preparation
Tahapan data preparation merupakan langkah penting dalam membangun sistem rekomendasi, karena kualitas data yang digunakan akan sangat memengaruhi kualitas hasil rekomendasi yang dihasilkan. Proses ini bertujuan untuk membersihkan, menyeleksi, dan mempersiapkan data agar siap digunakan dalam proses modeling.
Berikut adalah langkah-langkah data preparation yang dilakukan, sesuai urutan dalam notebook:
1. Import library

Pada tahap awal, dilakukan import library penting seperti `pandas` dan `numpy` untuk manipulasi data, serta `matplotlib`, `seaborn`, dan `WordCloud` untuk visualisasi. `TfidfVectorizer` dan `cosine_similarity` dari `sklearn` digunakan untuk menghitung kemiripan dalam sistem rekomendasi berbasis konten. Library ini mendukung proses pembersihan data, analisis, visualisasi, dan pembuatan model rekomendasi.

```python
# Import libraries
# Import libraries basic
import os
import pandas as pd
import numpy as np
import zipfile
import matplotlib.pyplot as plt
import seaborn as sns
sns.set_theme(style="ticks")
pd.set_option('display.max_colwidth', 50)

# visualisi
from wordcloud import WordCloud
from IPython.display import display

# prepocesing data
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity

# evaluasi
from itertools import combinations
```
2. Data loaading dataset
   
Dataset diunduh langsung dari GitHub dalam format CSV yang berisi data lagu Spotify. Setelah itu, data dibaca menggunakan ```pd.read_csv()``` dan ditampilkan beberapa baris awal dengan .```head()``` serta dilihat ukuran datanya dengan ```.shape()```. Alasan memastikan data berhasil dimuat dan memahami struktur serta ukuran data awal yang akan digunakan.
```python
# dwonload data
url = "https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2020/2020-01-21/spotify_songs.csv"
data = pd.read_csv(url)
```
```python
# baca data
data.head()
```
```python
# lihat jumlah data
print(data.shape)
```
3. Cek informasi dataset

Data diperiksa menggunakan ```.info()``` untuk mengetahui jumlah kolom, tipe data, dan nilai non-null. Selain itu, digunakan juga ```.describe()``` untuk mendapatkan ringkasan statistik seperti mean, min, dan max dari fitur numerik. Alasan untuk mengenali karakteristik data, melihat potensi anomali, serta mengidentifikasi apakah data memiliki tipe atau nilai yang perlu diubah.
```python
# cek info dataset
df.info()
# analisis statistik deskriptif
df.describe()
```
4. Cek missing value

Diperiksa jumlah missing value pada setiap kolom menggunakan ```.isna().sum()```. Data yang memiliki nilai kosong pada kolom penting seperti track_name, ```track_artist```, dan ```track_album_name``` dihapus menggunakan ```.dropna()```. Alasan data tersebut penting dalam sistem rekomendasi berbasis konten. Jika tidak lengkap, akan mengganggu akurasi perhitungan kemiripan antar lagu.
```python
# cek missing value
print(df.isna().sum())
```
```python
# Hapus missing value
df.dropna(subset=['track_name', 'track_artist', 'track_album_name'], inplace=True)
print(df.isnull().sum())
```
5. Cek duplikasi data

Duplikasi dicek menggunakan ```.duplicated().sum()``` untuk mengetahui apakah ada entri lagu yang muncul lebih dari sekali. Alasan duplikasi dapat menyebabkan bias pada sistem rekomendasi karena satu lagu bisa lebih diunggulkan tanpa alasan jelas, sehingga perlu dihindari.
```python
# cek duplikasi data
print('Duplikasi data ada: ', df.duplicated().sum())
```
6. Pengambilan Sampel Data

Pengambilan sampel dilakukan menggunakan `.sample(n=1500)` untuk memilih 1500 baris data secara acak dari dataset asli guna efisiensi proses eksplorasi dan pelatihan awal.
```python
# pengambilan sampel data sebanyak 1500 baris
df_sample = df.sample(n=1500, random_state=42)
```
7. Transformasi Fitur Durasi ke Satuan Menit

Fitur `duration_ms` yang semula dalam satuan milidetik diubah menjadi satuan menit agar lebih mudah dibaca dan dianalisis. Transformasi ini dilakukan dengan membagi nilai `duration_ms` dengan 60.000 (karena 1 menit = 60.000 milidetik), lalu disimpan ke kolom baru `duration_min` dalam dataframe `cbf_df`. Transformasi ini membantu dalam visualisasi dan interpretasi durasi lagu, serta dapat digunakan untuk analisis distribusi atau pengelompokan berdasarkan panjang lagu.
```python
# transformasi durasi dari milidetik ke menit
cbf_df['duration_min'] = cbf_df['duration_ms'] / 60000
cbf_df[['track_name', 'duration_ms', 'duration_min']].head()
```
8. Pembuatan Fitur-Fitur Baru (Feature Engineering)

Dilakukan proses rekayasa fitur untuk mengubah fitur numerik menjadi fitur kategorikal yang lebih interpretatif dan mendukung analisis berbasis konten. Beberapa fitur yang dibuat antara lain:
- duration_label: Kategori durasi lagu (pendek, sedang, panjang) berdasarkan nilai duration_min.
- energy_level: Kategori tingkat energi lagu (rendah, sedang, tinggi) berdasarkan nilai energy.
- danceability_level: Kategori tingkat keterdansaan lagu (rendah, sedang, tinggi) berdasarkan nilai danceability.
Kategorisasi dilakukan menggunakan aturan berbasis threshold sederhana (misalnya menggunakan pd.cut atau logika kondisional), agar fitur numerik menjadi representasi kategorikal yang mudah dikelompokkan dan dibandingkan antar lagu.
Berikut penjelasan yang kamu minta, dengan gaya yang konsisten seperti bagian-bagian sebelumnya:

9. Pembuatan Fitur Gabungan (`combined_features`) untuk Representasi Teks

Untuk mendukung pendekatan Content-Based Filtering berbasis teks, beberapa fitur kategorikal yang merepresentasikan karakteristik lagu digabungkan menjadi satu kolom teks. Fitur ini diberi nama `combined_features`, dan menjadi **input utama untuk proses ekstraksi vektor menggunakan TF-IDF**.
Fitur-fitur yang digabung meliputi:

* `track_name`
* `track_artist`
* `playlist_genre`
* `playlist_subgenre`
* `duration_label`
* `energy_level`
* `danceability_level`

Gabungan ini membentuk deskripsi semu setiap lagu, sehingga TF-IDF dapat mengenali kemiripan antar lagu berdasarkan konten.

```python
# gabungkan beberapa fitur kategorikal menjadi satu kolom teks
cbf_df['combined_features'] = (
    cbf_df['track_name'] + ' ' +
    cbf_df['track_artist'] + ' ' +
    cbf_df['playlist_genre'] + ' ' +
    cbf_df['playlist_subgenre'] + ' ' +
    cbf_df['duration_label'] + ' ' +
    cbf_df['energy_level'] + ' ' +
    cbf_df['danceability_level']
)
```
Fitur `combined_features` ini kemudian akan diproses lebih lanjut dengan TF-IDF Vectorizer untuk menghitung kemiripan antar lagu secara otomatis berdasarkan deskripsi kontennya.

10. Seleksi Fitur untuk Content-Based Filtering

Dilakukan seleksi fitur yang relevan untuk model Content-Based Filtering, yaitu kombinasi fitur numerik dan kategorikal yang mewakili karakteristik lagu. Fitur ini disimpan dalam variabel `cbf_features`, lalu dibuat dataframe `cbf_df` sebagai basis analisis kemiripan.
```python
# seleksi fitur untuk content-based filtering
cbf_data = cbf_df[['track_id', 'track_name', 'track_artist', 'playlist_genre', 'playlist_subgenre', 'duration_label', 'energy_level', 'danceability_level', 'combined_features']]
cbf_data.head()
```
11. Ekstraksi Fitur Teks dengan TF-IDF

Dilakukan proses ekstraksi fitur teks dari kolom `combined_features` menggunakan **TF-IDF Vectorizer** untuk merepresentasikan setiap lagu sebagai vektor numerik berbasis konten.

Langkah-langkah utama:

* **Mengatur ulang indeks** agar urut dan konsisten untuk keperluan indexing.
* **Inisialisasi dan fitting** `TfidfVectorizer` ke kolom `combined_features`.
* **Transformasi ke matriks TF-IDF** untuk menghitung bobot kata-kata penting.
* **Konversi ke bentuk matriks dense** dan simpan sebagai dataframe `df_tfidf` dengan `track_name` sebagai indeks.

```python
from sklearn.feature_extraction.text import TfidfVectorizer

# Mengatur ulang indeks agar urut dan konsisten untuk keperluan indexing
cbf_data = cbf_data.reset_index(drop=True)

# inisialisasi dan fit vectorizer
vectorizer = TfidfVectorizer(stop_words='english', max_df=0.95, min_df=2)
tfidf_matrix = vectorizer.fit_transform(cbf_data['combined_features'])

# ubah ke bentuk dense dan simpan sebagai DataFrame
dense_matrix = tfidf_matrix.todense()
df_tfidf = pd.DataFrame(
    dense_matrix,
    columns=vectorizer.get_feature_names_out(),
    index=cbf_data['track_name']
)
```
12. Perhitungan Kemiripan Lagu dengan Cosine Similarity

Kemiripan antar lagu dihitung menggunakan **Cosine Similarity** berdasarkan hasil vektorisasi TF-IDF. Fungsi `cosine_similarity` dari `sklearn` digunakan untuk menghasilkan matriks kemiripan antar semua lagu. Matriks `cosine_sim` ini menjadi dasar untuk memberikan rekomendasi lagu berdasarkan kemiripan kontennya.
```python
from sklearn.metrics.pairwise import cosine_similarity

# hitung cosine similarity dari tf-idf matrix
cosine_sim = cosine_similarity(tfidf_matrix)

# cek ukuran matriks hasil
print(cosine_sim.shape)
```

----------------------------------------------------


## Modeling
Pada tahap modeling, dibuat sistem rekomendasi berbasis Content-Based Filtering untuk menyelesaikan masalah menemukan lagu-lagu yang mirip dengan lagu yang disukai pengguna. Sistem ini menggunakan fitur  track_id, track_name, track_artist, playlist_genre, playlist_subgenre, duration_label, energy_level dan danceability_level dari lagu-lagu Spotify sebagai representasi konten. Sistem rekomendasi untuk membantu pengguna menemukan lagu-lagu baru berdasarkan kemiripan dengan lagu yang disukai dengan keyword pilihan id musik, genre dan judul lagu serta keyword kata.

<div align="center">
<img width="500" alt="Alur Sistem Rekomendasi Bekerja" src="https://github.com/user-attachments/assets/3beb8dd7-0e0c-463f-b662-4b225e9079d5" />
<br/>
<strong>Gambar 3.</strong> Alur Sistem Rekomendasi Bekerja
</div>

Sistem dapat memberikan rekomendasi berupa daftar top-N lagu yang paling mirip berdasarkan nilai kemiripan dengan lagu yang dipilih pengguna. Misalnya, jika pengguna memilih lagu “Love Yourself” dari Justin Bieber, maka sistem akan merekomendasikan lagu-lagu lain dengan genre yang memiliki tingkat kemiripan tertinggi. Sistem ini secara otomatis menghasilkan rekomendasi yang relevan dengan preferensi lagu pengguna tanpa membutuhkan data interaksi pengguna lain. Hasil rekomendasi ini divisualisasikan dalam bentuk tabel yang menampilkan lagu-lagu yang direkomendasikan beserta nama artis, album, dan skor kemiripan (similarity score). Skor kemiripan menunjukkan seberapa dekat karakteristik lagu tersebut dengan lagu referensi, dengan nilai berkisar antara 0 (tidak mirip) sampai 1 (sangat mirip). Berikut adalah kode program fungsi rekomendasi:

```python
# Menghasilkan top_n rekomendasi berdasarkan kemiripan konten, beserta skor similarity
def cbf_product_recommendations(id_product, similarity_data=cosine_sim, items=cbf_data, top_n=10):
    index = items.index[items.track_id == id_product][0]  # Dapatkan indeks produk
    sim_scores = list(enumerate(similarity_data[index]))  # Skor similarity dengan semua item
    sim_scores = sorted(sim_scores, key=lambda x: x[1], reverse=True)  # Urutkan dari paling mirip
    return sim_scores[1:top_n+1]  # Ambil top_n hasil (kecuali diri sendiri)
```

### Hasil Rekoemndasi (Input Judul Musik): 
Pada test ini sistem diuji dengan memakai input keyword judul musik, sistem akan merekomendasikan musik dengan genre yang mirip.

**Kode Program**
```python
# Input nama lagu atau sebagian nama
track_name_input = "Losers"

# Cari lagu yang cocok
matching_tracks = cbf_data[cbf_data['track_name'].str.contains(track_name_input, case=False, na=False)]

if matching_tracks.empty:
    print("Lagu tidak ditemukan.")
else:
    # Ambil lagu pertama yang cocok
    selected_track_id = matching_tracks.iloc[0]['track_id']
    selected_track_name = matching_tracks.iloc[0]['track_name']

    print(f"Lagu ditemukan: {selected_track_name} (track_id: {selected_track_id})")
    print(f"\nRekomendasi untuk lagu: {selected_track_name}\n")

    # Ambil hasil rekomendasi dan similarity score
    recommended = cbf_product_recommendations(selected_track_id, cosine_sim, cbf_data, top_n=10)

    # Ambil index dan skor
    recommended_indices = [i[0] for i in recommended]
    similarity_scores = [i[1] for i in recommended]

    # Ambil data lagu berdasarkan index
    recommended_tracks = cbf_data.iloc[recommended_indices][['track_id', 'track_name', 'playlist_genre', 'playlist_subgenre']].copy()
    recommended_tracks['similarity_score'] = similarity_scores

    # Tampilkan hasil
    display(recommended_tracks.reset_index(drop=True))
```
**Output ini adalah 🎶 Daftar judul Lagu**

**Rekomendasi Musik untuk Lagu: `Losers`**  

**Track ID:** `3kE5NmMUCPLw5sbWxUQToU`  

**Genre:** Pop

**Jumlah rekomendasi:** 10 lagu

**Daftar Lagu Rekomendasi**

| track\_id              | track\_name     | playlist\_genre | playlist\_subgenre | similarity\_score |
| ---------------------- | --------------- | --------------- | ------------------ | ----------------- |
| 4kRT3cCwp0uYEqh4hHvxZS | Jimmy           | pop             | post-teen pop      | 1.000000          |
| 1mRBJdpIgc3jZH8C3cN2WV | If Only         | pop             | post-teen pop      | 1.000000          |
| 03teNQu8rWlFnNzF1ULXIq | Starstruck      | pop             | post-teen pop      | 0.957938          |
| 2fQxE0jVrjNMT9oJAXtSJR | Domino          | pop             | post-teen pop      | 0.957696          |
| 2NjhV99ncY4A5lSkTHvTtU | Lollipop        | pop             | post-teen pop      | 0.957696          |
| 5WpNa4vUaruzh0KISY4NkN | Glory           | pop             | post-teen pop      | 0.954205          |
| 6xg61PHNCLvQClEJrT9p0V | What it Takes   | pop             | post-teen pop      | 0.915788          |
| 52vS7mJ0a70Z4uRCfl8SjH | What About Love | pop             | post-teen pop      | 0.849303          |
| 06wxsDleir1dIlqeNv6m2M | You Said        | pop             | post-teen pop      | 0.766997          |
| 0gJvqi9QyASOCtJu99tytc | Because of You  | pop             | post-teen pop      | 0.753952          |


**Analisa:**

Rekomendasi didominasi oleh lagu-lagu dengan genre **pop** dan subgenre **post-teen pop**, menunjukkan sistem fokus pada kesamaan genre dan gaya musik yang sangat spesifik. Dua lagu teratas memiliki skor similarity sempurna 1.0, menandakan kemiripan identik dengan lagu acuan.

Skor similarity secara bertahap menurun dari sekitar 0.95 hingga 0.75, yang menunjukkan variasi tingkat kemiripan namun masih dalam batas yang cukup dekat. Hal ini mengindikasikan sistem berhasil memberikan rekomendasi lagu yang relevan dan seragam dari segi konten dan gaya musik.

Secara keseluruhan, hasil ini menunjukkan sistem rekomendasi efektif dalam menyajikan lagu-lagu yang sangat mirip berdasarkan fitur audio dan metadata yang digunakan, khususnya dalam genre dan subgenre yang dipilih.


### Hasil Rekoemndasi (Input Genre Musik):
Berikut ini adalah keyword Genre yang digunakan dalam uji coba ini sesuai dengan genre yang ada di datset rap, edm, pop, r&b, latin dan rock.

**Kode Program**
```python
# Input keyword genre
keyword_genre = "latin"

# Jumlah maksimum lagu yang ingin ditampilkan
top_n = 10

# Filter lagu-lagu yang genre-nya mengandung keyword
filtered_songs = cbf_data[cbf_data['playlist_genre'].str.contains(keyword_genre, case=False, na=False)]

if filtered_songs.empty:
    print(f"Tidak ditemukan lagu dengan genre '{keyword_genre}'.")
else:
    print(f"Lagu dengan genre '{keyword_genre}'")

    # Ambil satu lagu acuan (misalnya lagu pertama)
    reference_track_id = filtered_songs.iloc[0]['track_id']
    reference_track_name = filtered_songs.iloc[0]['track_name']

    print(f"Lagu acuan: {reference_track_name} (track_id: {reference_track_id})")

    # Dapatkan rekomendasi berdasarkan lagu acuan
    recommended = cbf_product_recommendations(reference_track_id, cosine_sim, cbf_data, top_n=top_n)

    # Ambil index dan skor similarity
    recommended_indices = [i[0] for i in recommended]
    similarity_scores = [i[1] for i in recommended]

    # Ambil data lagu dan tambahkan skor similarity
    recommended_tracks = cbf_data.iloc[recommended_indices][['track_id', 'track_name', 'playlist_genre', 'playlist_subgenre']].copy()
    recommended_tracks['similarity_score'] = [round(score, 3) for score in similarity_scores]

    # Tampilkan hasil
    display(recommended_tracks.reset_index(drop=True))
```
**Output ini adalah 🎶 Daftar Lagu dengan Genre Latin**

**Rekomendasi Musik Berdasarkan Genre: `latin`**

**Jumlah rekomendasi:** 10 lagu

**Daftar Lagu Rekomendasi**

| track\_id              | track\_name                      | playlist\_genre | playlist\_subgenre | similarity\_score |
| ---------------------- | -------------------------------- | --------------- | ------------------ | ----------------- |
| 4xvTPuwHaXoDM3p0QcY7bH | Música                           | latin           | reggaeton          | 0.904             |
| 2RNvcU4iA11QdWnfGbTnzr | Legendary (DJ Kantik Remix)      | latin           | latin hip hop      | 0.527             |
| 0WZqP2WahJbKURqUK3fBPk | Eternamente Bella                | latin           | latin pop          | 0.510             |
| 23YEpFgAVvr0w3cDm7EQ1Q | Prrrum                           | latin           | latin pop          | 0.510             |
| 0KzhyaVtr2v4J9GVdMgCk0 | Gangsta                          | latin           | latin pop          | 0.479             |
| 5djZm1zFGcJUSUqbBjrAZH | O Saki Saki (From "Batla House") | latin           | latin pop          | 0.459             |
| 3sFX86i3Qebco0KhrUVCoL | FWB                              | latin           | latin pop          | 0.447             |
| 3qSLaqWAsUdpf830MjlRTm | Yo Sé                            | latin           | latin hip hop      | 0.433             |
| 4gWAcvkVLzqnzFOcrYBut7 | Choosy (feat. Jeremih & Davido)  | latin           | latin pop          | 0.427             |
| 7sBDv4kLo2GVucy5VGh7GX | A punto (feat. Delfina Campos)   | latin           | latin pop          | 0.425             |


**Analisa Singkat dengan Konteks Input Genre:**

Sistem rekomendasi ini bekerja dengan menggunakan input pencarian berdasarkan **genre**, sehingga hasil rekomendasi didominasi oleh lagu-lagu dalam genre **latin** yang sama dengan lagu acuan. Hal ini terlihat dari konsistensi genre dan subgenre pada daftar rekomendasi, seperti latin pop dan latin hip hop.

Pendekatan ini efektif untuk memberikan rekomendasi yang relevan secara tematik, menjaga kesamaan gaya musik sesuai preferensi pengguna yang memilih genre tertentu sebagai input. Skor similarity yang berbeda-beda mencerminkan tingkat kedekatan lagu-lagu tersebut dengan lagu input dalam konteks fitur audio dan metadata yang digunakan.


----------------------------------------------------


## Evaluation


## Kesimpulan

1. Kelebihan pendekatan Content-Based Filtering ini adalah kemampuannya untuk memberikan rekomendasi yang sangat personal karena langsung menganalisis fitur konten lagu. Sistem tidak bergantung pada data interaksi pengguna lain sehingga efektif untuk skenario dengan data pengguna terbatas.
Kekurangannya adalah sistem cenderung merekomendasikan lagu-lagu yang mirip dengan apa yang sudah diketahui pengguna dan kurang mampu menawarkan rekomendasi lagu yang benar-benar baru atau berbeda (masalah eksplorasi). Secara keseluruhan, pendekatan ini sudah efektif untuk menghasilkan rekomendasi yang relevan dan dapat menjadi fondasi untuk pengembangan sistem rekomendasi yang lebih kompleks di masa depan.
