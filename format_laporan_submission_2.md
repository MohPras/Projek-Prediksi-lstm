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
2. Bagaimana mengukur seberapa baik sistem rekomendasi yang dibangun dalam menyajikan hasil yang relevan dan akurat?
3. Berapa total jumlah playlist ID yang tersedia?
4. Berapa banyak lagu unik yang terdapat dalam dataset?
5. Lagu mana yang paling sering muncul dalam playlist?
6. Lagu mana yang paling jarang muncul dalam playlist?
7. Berapa total nama lagu yang tercatat?
8. Lagu apa yang paling populer di Spotify berdasarkan data ini?
9. Berapa jumlah playlist unik yang ada?
10. Berapa banyak genre utama yang ditemukan?
11. Berapa banyak subgenre yang terdapat dalam dataset?
12. Genre apa yang paling sering muncul?
13. Subgenre apa yang paling sering muncul?
14. Siapa artis dengan jumlah lagu paling banyak didengar?
15. Lagu mana yang memiliki durasi paling panjang?
16. Lagu mana yang memiliki durasi paling pendek?

### Goals
Tujuan dari proyek ini adalah:
1. Mengembangkan sistem rekomendasi musik yang mampu memberikan daftar rekomendasi lagu berdasarkan input lagu tertentu seperti id musik, genre dan keyword nama lagu.
2. Mengimplementasikan pendekatan Content-Based Filtering untuk menghasilkan Top-N recommendation yang akurat.
3. Melakukan eksplorasi data untuk menjawab pertanyaan dari point masalah utama nomer 3 sampai 16.

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
   
Pada proyek ini kolom yang digunakan sebagai berikut:
- **track\_id** – ID unik untuk tiap lagu
- **track\_name** – Nama lagu
- **track\_artist** – Nama artis penyanyi
- **playlist\_genre** – Genre utama playlist
- **playlist\_subgenre** – Subgenre dari playlist
- **duration\_label** – Kategori durasi lagu (mis. pendek/sedang/panjang)
- **energy\_level** – Tingkat energi lagu (rendah hingga tinggi)
- **danceability\_level** – Tingkat kemudahan untuk berdansa
- **combined\_features** – Gabungan fitur numerik untuk analisis
Dataset ini sudah cukup bersih dan tidak memiliki banyak nilai kosong. Namun, tetap dilakukan pemeriksaan dan eksplorasi untuk memastikan kualitas data.

### Eksplorasi Data & Visualisasi Data
Beberapa langkah exploratory data analysis (EDA) dilakukan untuk memahami distribusi dan hubungan antar fitur dan dibawah ini adalah resmue dari beberapa tahapan yang sudah dilakukan. kode dibawah ini adalah kode untuk membuat resum pada analisis eda yang sudah dilakukan, disarankan untuk melihat code keseluruhan pada file ipynb agar tidak terjadi eror. Berikut ini kodenya:
```
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
Pada tahap awal, dilakukan import berbagai library yang dibutuhkan seperti ```pandas, numpy, matplotlib, seaborn, sklearn```, dan beberapa modul dari keras serta ```tensorflow```. Library ini digunakan untuk manipulasi data, visualisasi, dan perhitungan similarity. Meskipun library seperti ResNet50 dan ```keras.layers diimpor```, tidak semua digunakan dalam proses content-based filtering, kemungkinan dipersiapkan untuk eksperimen lanjutan. Alasan Menyediakan semua tools yang diperlukan untuk data cleaning, analisis, dan model building.
```
# Import libraries
import tensorflow as tf
from tensorflow import keras
from keras import layers
from keras.applications.resnet50 import preprocess_input, ResNet50
import os
import pandas as pd
import numpy as np
import zipfile
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.metrics import ConfusionMatrixDisplay, classification_report
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity
from IPython.display import display

sns.set_theme(style="ticks")
pd.set_option('display.max_colwidth', 50)
```
2. Data loaading dataset
Dataset diunduh langsung dari GitHub dalam format CSV yang berisi data lagu Spotify. Setelah itu, data dibaca menggunakan ```pd.read_csv()``` dan ditampilkan beberapa baris awal dengan .```head()``` serta dilihat ukuran datanya dengan ```.shape()```. Alasan memastikan data berhasil dimuat dan memahami struktur serta ukuran data awal yang akan digunakan.
```
# dwonload data
url = "https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2020/2020-01-21/spotify_songs.csv"
data = pd.read_csv(url)
```
```
# baca data
data.head()
```
```
# lihat jumlah data
print(data.shape)
```
3. Cek informasi dataset
Data diperiksa menggunakan ```.info()``` untuk mengetahui jumlah kolom, tipe data, dan nilai non-null. Selain itu, digunakan juga ```.describe()``` untuk mendapatkan ringkasan statistik seperti mean, min, dan max dari fitur numerik. Alasan untuk mengenali karakteristik data, melihat potensi anomali, serta mengidentifikasi apakah data memiliki tipe atau nilai yang perlu diubah.
```
# cek info dataset
df.info()
# analisis statistik deskriptif
df.describe()
```
4. Cek missing value
Diperiksa jumlah missing value pada setiap kolom menggunakan ```.isna().sum()```. Data yang memiliki nilai kosong pada kolom penting seperti track_name, ```track_artist```, dan ```track_album_name``` dihapus menggunakan ```.dropna()```. Alasan data tersebut penting dalam sistem rekomendasi berbasis konten. Jika tidak lengkap, akan mengganggu akurasi perhitungan kemiripan antar lagu.
```
# cek missing value
print(df.isna().sum())
```
```
# Hapus missing value
df.dropna(subset=['track_name', 'track_artist', 'track_album_name'], inplace=True)
print(df.isnull().sum())
```
6. Cek duplikasi data
Duplikasi dicek menggunakan ```.duplicated().sum()``` untuk mengetahui apakah ada entri lagu yang muncul lebih dari sekali. Alasan duplikasi dapat menyebabkan bias pada sistem rekomendasi karena satu lagu bisa lebih diunggulkan tanpa alasan jelas, sehingga perlu dihindari.
```
# cek duplikasi data
print('Duplikasi data ada: ', df.duplicated().sum())
```

----------------------------------------------------


## Modeling
Pada tahap modeling, dibuat sistem rekomendasi berbasis Content-Based Filtering untuk menyelesaikan masalah menemukan lagu-lagu yang mirip dengan lagu yang disukai pengguna. Sistem ini menggunakan fitur  track_id, track_name, track_artist, playlist_genre, playlist_subgenre, duration_label, energy_level dan danceability_level dari lagu-lagu Spotify sebagai representasi konten. Data object diubah ke numerik serta beberapa kolom dilakukan penggabungan untuk mendapatkan representasi data yang bagus. Teknik TF-IDF Vectorization diterapkan untuk mengubah teks genre menjadi vektor numerik, sehingga memungkinkan perhitungan kemiripan antar lagu menggunakan metode cosine similarity. Sistem rekomendasi untuk membantu pengguna menemukan lagu-lagu baru berdasarkan kemiripan dengan lagu yang disukai dengan keyword pilihan id musik, genre dan judul lagu serta keyword kata.

<div align="center">
<img width="500" alt="Alur Sistem Rekomendasi Bekerja" src="https://github.com/user-attachments/assets/3beb8dd7-0e0c-463f-b662-4b225e9079d5" />
<br/>
<strong>Gambar 3.</strong> Alur Sistem Rekomendasi Bekerja
</div>

Setelah proses vektorisasi, sistem dapat memberikan rekomendasi berupa daftar top-N lagu yang paling mirip berdasarkan nilai kemiripan dengan lagu yang dipilih pengguna. Misalnya, jika pengguna memilih lagu “Love Yourself” dari Justin Bieber, maka sistem akan merekomendasikan lagu-lagu lain dengan genre yang memiliki tingkat kemiripan tertinggi. Sistem ini secara otomatis menghasilkan rekomendasi yang relevan dengan preferensi lagu pengguna tanpa membutuhkan data interaksi pengguna lain. Hasil rekomendasi ini divisualisasikan dalam bentuk tabel yang menampilkan lagu-lagu yang direkomendasikan beserta nama artis, album, dan skor kemiripan (similarity score). Skor kemiripan menunjukkan seberapa dekat karakteristik lagu tersebut dengan lagu referensi, dengan nilai berkisar antara 0 (tidak mirip) sampai 1 (sangat mirip).

### Hasil Rekomendasi (Input ID Musik): 
**Kode Program**
```
from IPython.display import display

# Ambil input nama id track
product_name_input = "06UXtRLTF6kdMSM3uaVCCU"

# Mencari product_id berdasarkan nama produk
matching_products = cbf_data[cbf_data['track_id'].str.contains(product_name_input, case=False, na=False, regex=False)]

if matching_products.empty:
    print("Musik tidak ditemukan.")
else:
    sample_product_id = matching_products['track_id'].values[0]
    print(f"Track ID untuk '{product_name_input}': {sample_product_id}")

    # Mendapatkan indeks rekomendasi dari fungsi
    recommended_indices = cbf_product_recommendations(sample_product_id)
    print(f"Jumlah rekomendasi: {len(recommended_indices)}")  # Menampilkan jumlah rekomendasi

    # Menampilkan rekomendasi produk berdasarkan indeks
    recommended_products = cbf_data.iloc[recommended_indices][['track_id', 'track_name', 'playlist_genre', 'playlist_subgenre']]

    # Menampilkan pengaturan untuk tampilan yang lebih baik
    pd.set_option('display.max_rows', None)  # Menampilkan semua baris
    pd.set_option('display.max_columns', None)  # Menampilkan semua kolom
    pd.set_option('display.width', None)  # Menyesuaikan lebar tampilan
    pd.set_option('display.max_colwidth', None)  # Menampilkan panjang kolom penuh

    print("\nRecommended Music:")

    # Menampilkan tabel dengan menggunakan display untuk format yang rapi di Google Colab
    display(recommended_products)
```
**Output Berikut ini adalah 🎵 Top-N Rekomendasi Musik Berdasarkan Content-Based Filtering**

**Rekomendasi Musik untuk Track ID `06UXtRLTF6kdMSM3uaVCCU`**

**Jumlah rekomendasi:** 10 lagu

**Daftar Lagu Rekomendasi**


| No. | Track ID                      | Judul Lagu                                 | Genre | Subgenre   |
|-----|-------------------------------|--------------------------------------------|--------|-------------|
| 1   | 1qP7KmHJbzvV8KsFPhW8wY        | Seven Seas Of Rhye - Remastered 2011       | rock   | album rock  |
| 2   | 62daWSLgfeezIl4MTQFb08        | The Millionaire Waltz - Remastered 2011    | rock   | album rock  |
| 3   | 6PT7wUJefYPEU1lX1lcLRJ        | Doing Alright - Remastered 2011            | rock   | album rock  |
| 4   | 26FJA5apYWeehOGnZdUPob        | Body Language - Remastered 2011            | rock   | album rock  |
| 5   | 2ISPUUp4pzssWuR2Ic09vR        | God Save The Queen - Remastered 2011       | rock   | album rock  |
| 6   | 489S9D7zr1jSMlNZHLnKKX        | Stone Cold Crazy - Remastered 2011         | rock   | album rock  |
| 7   | 5txoZyuAmtCfmDjUCEphWm        | Somebody To Love - 2011 Mix                | rock   | hard rock   |
| 8   | 42qlo3Oi69rOnHMmOKB8uq        | Singularity                                 | rock   | album rock  |
| 9   | 3x2bXiU0o4WbsPkawXlfDA        | Who Are You                                 | rock   | album rock  |
| 10  | 1Q2fYlSdwuutWj3QplhY9q        | Riot                                        | rock   | hard rock   |

**Ringkasan Genre/Subgenre**

- **Genre dominan:** Rock
- **Subgenre terbanyak:** Album Rock (8 lagu)
- **Subgenre lainnya:** Hard Rock (2 lagu)

*Catatan: Rekomendasi ini dihasilkan menggunakan pendekatan Content-Based Filtering berdasarkan kemiripan fitur lagu dengan track input.*


### Hasil Rekoemndasi (Input Genre Musik):
Berikut ini adalah keyword Genre yang digunakan dalam uji coba ini sesuai dengan genre yang ada di datset rap, edm, pop, r&b, latin dan rock.

**Kode Program**
```
from IPython.display import display

# Input keyword genre
keyword_genre = "latin"

# Jumlah maksimum lagu yang ingin ditampilkan (otomatis sesuai top_n dari sistem rekomendasi)
top_n = 10

# Filter lagu-lagu yang genre-nya mengandung keyword genre (case insensitive)
filtered_songs = cbf_data[cbf_data['playlist_genre'].str.contains(keyword_genre, case=False, na=False)]

if filtered_songs.empty:
    print(f"Tidak ditemukan lagu dengan genre '{keyword_genre}'.")
else:
    print(f"Lagu dengan genre '{keyword_genre}'")
    print(f"Jumlah rekomendasi: {min(top_n, len(filtered_songs))}")

    # Pengaturan tampilan agar lebih rapi
    pd.set_option('display.max_rows', None)
    pd.set_option('display.max_columns', None)
    pd.set_option('display.width', None)
    pd.set_option('display.max_colwidth', None)

    # Tampilkan hingga top_n lagu (jika tersedia)
    display(filtered_songs[['track_id', 'track_name', 'playlist_genre', 'playlist_subgenre']].head(top_n))
```
**Output ini adalah 🎶 Daftar Lagu dengan Genre Latin**

**Rekomendasi Musik Berdasarkan Genre: `latin`**

**Jumlah rekomendasi:** 10 lagu

**Daftar Lagu Rekomendasi**

| No. | Track ID                      | Judul Lagu                            | Genre | Subgenre       |
|-----|-------------------------------|----------------------------------------|--------|----------------|
| 1   | 4xvTPuwHaXoDM3p0QcY7bH        | Música                                 | latin | latin pop      |
| 2   | 34v7cD6VR3fVYguedQ1wuh        | Tropical Forest                         | latin | tropical       |
| 3   | 53rhwRKKrsWaT6tuSzymdY        | mEnorme                                 | latin | tropical       |
| 4   | 7LRJmZ6G5qHQEG2CGeTCji        | We Can (feat. Tory Lanez)              | latin | latin hip hop  |
| 5   | 7MRU4vOkywuhZ9kbFiPuiu        | Si Supieras                             | latin | latin hip hop  |
| 6   | 35FIDQv0u26DSknDahmcdz        | With You                                | latin | tropical       |
| 7   | 3ALLv1BQxYFlJ8XQOQtgW1        | DIEZ MINUTOS (feat. Mario Bautista)    | latin | latin pop      |
| 8   | 3uYzfyifC7J1j1IEjN1xz6        | This Love - Acoustic                    | latin | latin pop      |
| 9   | 3BffVF4K7OelPuo46KUqhe        | Ella Me Levanto                         | latin | reggaeton      |
| 10  | 7yws3pF3FFguwT2Psi6c15        | Do You Remember                         | latin | latin hip hop  |

**Ringkasan Genre/Subgenre**

- **Genre dominan:** Latin
- **Subgenre terbanyak:**  
  - *Latin Pop*: 3 lagu  
  - *Tropical*: 3 lagu  
  - *Latin Hip Hop*: 3 lagu  
  - *Reggaeton*: 1 lagu
    
*Catatan: Rekomendasi ini dihasilkan menggunakan pendekatan Content-Based Filtering berdasarkan lagu-lagu yang memiliki genre `latin`.*


### Hasil Rekoemndasi (Input Judul Musik): 
Pada test ini sistem diuji dengan memakai input keyword musik misal ( what, who, and, you dst) selain dengan keyword itu pada test ini juga bisa melakukan rekomendasi berdasar judul lagu yang dimasukan.
**Kode Program**
```
from IPython.display import display

def get_track_id_by_name(name, data):
    matches = data[data['track_name'].str.contains(name, case=False, na=False)]
    return matches

# Masukan nama lagu disini atau keyword
# contoh nama lagu : I Miss You
# contoh keyword : what/word/who dst
track_name_input = "what"

matching_tracks = get_track_id_by_name(track_name_input, cbf_data)

if matching_tracks.empty:
    print("Lagu tidak ditemukan.")
else:
    # Ambil lagu pertama yang cocok langsung
    selected_track_id = matching_tracks.iloc[0]['track_id']
    selected_track_name = matching_tracks.iloc[0]['track_name']

    print(f"Lagu ditemukan: {selected_track_name} (track_id: {selected_track_id})")
    print(f"\nRekomendasi untuk lagu: {selected_track_name}")

    top_n = 10
    recommended_indices = cbf_product_recommendations(
        id_product=selected_track_id, similarity_data=cosine_sim, items=cbf_data, top_n=top_n
    )

    print(f"Jumlah rekomendasi: {len(recommended_indices)}\n")

    recommended_tracks = cbf_data.iloc[recommended_indices][['track_id', 'track_name', 'playlist_genre', 'playlist_subgenre']]

    display(recommended_tracks.reset_index(drop=True))
```
**Output ini adalah 🎶 Daftar Lagu dengan Genre Latin**

**Rekomendasi Musik untuk Lagu: `Look What You Made Me Do`**  

**Track ID:** `1P17dC1amhFzptugyAO7Il`  

**Genre:** Pop

**Jumlah rekomendasi:** 10 lagu

**Daftar Lagu Rekomendasi**

| No. | Track ID                      | Judul Lagu          | Genre | Subgenre        |
|-----|-------------------------------|----------------------|--------|-----------------|
| 1   | 6xg61PHNCLvQClEJrT9p0V        | What it Takes        | pop    | post-teen pop   |
| 2   | 2fQxE0jVrjNMT9oJAXtSJR        | Domino               | pop    | post-teen pop   |
| 3   | 2NjhV99ncY4A5lSkTHvTtU        | Lollipop             | pop    | post-teen pop   |
| 4   | 03teNQu8rWlFnNzF1ULXIq        | Starstruck           | pop    | post-teen pop   |
| 5   | 3kE5NmMUCPLw5sbWxUQToU        | Losers               | pop    | post-teen pop   |
| 6   | 4kRT3cCwp0uYEqh4hHvxZS        | Jimmy                | pop    | post-teen pop   |
| 7   | 1mRBJdpIgc3jZH8C3cN2WV        | If Only              | pop    | post-teen pop   |
| 8   | 5WpNa4vUaruzh0KISY4NkN        | Glory                | pop    | post-teen pop   |
| 9   | 52vS7mJ0a70Z4uRCfl8SjH        | What About Love      | pop    | post-teen pop   |
| 10  | 09IStsImFySgyp0pIQdqAc        | The Middle           | pop    | post-teen pop   |

**Ringkasan Genre/Subgenre**

- **Genre utama:** Pop  
- **Subgenre dominan:** Post-Teen Pop (10 lagu)

*Catatan: Rekomendasi ini dibuat menggunakan Content-Based Filtering berdasarkan lagu `Look What You Made Me Do` dengan karakteristik genre/subgenre yang mirip.*


Kelebihan pendekatan Content-Based Filtering ini adalah kemampuannya untuk memberikan rekomendasi yang sangat personal karena langsung menganalisis fitur konten lagu. Sistem tidak bergantung pada data interaksi pengguna lain sehingga efektif untuk skenario dengan data pengguna terbatas.
Kekurangannya adalah sistem cenderung merekomendasikan lagu-lagu yang mirip dengan apa yang sudah diketahui pengguna dan kurang mampu menawarkan rekomendasi lagu yang benar-benar baru atau berbeda (masalah eksplorasi). Secara keseluruhan, pendekatan ini sudah efektif untuk menghasilkan rekomendasi yang relevan dan dapat menjadi fondasi untuk pengembangan sistem rekomendasi yang lebih kompleks di masa depan.


----------------------------------------------------


## Evaluation

### A. Evaluasi Hasil Rekomendasi Musik Berdasarkan Track ID
**Deskripsi Dataset dan Evaluasi**

Dataset yang digunakan berisi total 1500 lagu dengan berbagai genre dan subkategori. Pada evaluasi ini, dilakukan pengujian dengan memasukkan input lagu dengan Track ID 06UXtRLTF6kdMSM3uaVCCU untuk menghasilkan rekomendasi sebanyak 10 lagu.

**Hasil Rekomendasi**

Dari hasil rekomendasi yang diberikan, seluruh lagu yang direkomendasikan (10 lagu) termasuk dalam genre rock, dengan subkategori mayoritas album rock dan sebagian hard rock.

| Metrik                                 | Nilai                                     | Keterangan                                                         |
| -------------------------------------- | ----------------------------------------- | ------------------------------------------------------------------ |
| Jumlah rekomendasi                     | 10                                        | Total lagu yang direkomendasikan                                   |
| Lagu rekomendasi genre "rock"          | 10                                        | Semua lagu rekomendasi bergenre rock                               |
| Lagu rekomendasi subgenre "album rock" | 7                                         | 7 lagu subgenre album rock                                         |
| Lagu rekomendasi subgenre "hard rock"  | 3                                         | 3 lagu subgenre hard rock                                          |
| Presisi (Precision)                    | 10 / 10 = 1.00                            | Semua rekomendasi sesuai dengan genre input                        |
| Recall                                 | 10 / 240 = 0.0417 (4.17%)                 | Persentase lagu rock yang berhasil direkomendasikan                |
| Coverage                               | (10 / 240) × 100 = 4.17%                  | Persentase cakupan lagu dalam genre rock dari total genre rock     |
| Diversity                              | 2 subgenre dari total 24 subgenre ≈ 8.33% | Variasi subgenre yang muncul dalam rekomendasi dari total subgenre |

**Interpretasi Hasil**

- Presisi 100% menunjukkan semua lagu yang direkomendasikan benar-benar sesuai genre input (rock). Sistem sangat fokus dan akurat dalam genre yang sama.

- Recall 4.17% relatif rendah, karena sistem diseting hanya merekomendasikan top 10 lagu dari total 240 lagu rock yang ada di dataset. Ini wajar karena rekomendasi hanya top 10.

- Coverage 4.17% sama dengan recall dalam konteks genre ini, menandakan seberapa luas sistem merekomendasikan lagu dalam genre rock.

- Diversity 8.33% menunjukkan variasi subgenre dalam rekomendasi, yang masih terbatas karena hanya ada 2 subgenre dari total 24 subgenre yang ada. Artinya, rekomendasi cukup spesifik dan belum menawarkan banyak variasi.

**Kesimpulan**

Metode Content Based Filtering memberikan hasil rekomendasi dengan presisi tinggi (100%), sangat relevan dengan genre input. Namun, recall dan coverage rendah menandakan sistem hanya merekomendasikan sebagian kecil lagu dalam genre tersebut, sesuai dengan jumlah rekomendasi yang dibatasi yaitu (top 10). Variasi subgenre dalam rekomendasi masih terbatas, sehingga sistem perlu ditingkatkan untuk meningkatkan diversity agar rekomendasi lebih beragam.

### B. Evaluasi Hasil Rekomendasi Musik Berdasarkan Track ID
**Deskripsi Dataset dan Evaluasi**

Dataset yang digunakan berisi total 1500 lagu dengan berbagai genre dan subkategori. Pada evaluasi ini, dilakukan pengujian dengan memasukkan input lagu dengan genre latin untuk menghasilkan rekomendasi sebanyak 10 lagu.

**Hasil Rekomendasi**

Dari hasil rekomendasi yang diberikan, seluruh lagu yang direkomendasikan (10 lagu) termasuk dalam genre latin, dengan subkategori yang beragam yaitu latin pop, tropical, latin hip hop, dan reggaeton.

| Metrik                                    | Nilai                                      | Keterangan                                                         |
| ----------------------------------------- | ------------------------------------------ | ------------------------------------------------------------------ |
| Jumlah rekomendasi                        | 10                                         | Total lagu yang direkomendasikan                                   |
| Lagu rekomendasi genre "latin"            | 10                                         | Semua lagu rekomendasi bergenre latin                              |
| Lagu rekomendasi subgenre "latin pop"     | 3                                          | 3 lagu subgenre latin pop                                          |
| Lagu rekomendasi subgenre "tropical"      | 3                                          | 3 lagu subgenre tropical                                           |
| Lagu rekomendasi subgenre "latin hip hop" | 3                                          | 3 lagu subgenre latin hip hop                                      |
| Lagu rekomendasi subgenre "reggaeton"     | 1                                          | 1 lagu subgenre reggaeton                                          |
| Presisi (Precision)                       | 10 / 10 = 1.00                             | Semua rekomendasi sesuai dengan genre input                        |
| Recall                                    | 10 / 220 = 0.0455 (4.55%)                  | Persentase lagu latin yang berhasil direkomendasikan               |
| Coverage                                  | (10 / 220) × 100 = 4.55%                   | Persentase cakupan lagu dalam genre latin dari total genre latin   |
| Diversity                                 | 4 subgenre dari total 24 subgenre ≈ 16.67% | Variasi subgenre yang muncul dalam rekomendasi dari total subgenre |

**Interpretasi Hasil**

- Presisi 100% menunjukkan semua lagu yang direkomendasikan benar-benar sesuai genre input (latin). Sistem sangat akurat dalam memilih lagu dalam genre yang sama.

- Recall 4.55% relatif rendah, karena sistem hanya merekomendasikan top 10 lagu dari total 220 lagu latin yang ada di dataset. Ini sesuai dengan batasan jumlah rekomendasi.

- Coverage 4.55% sama dengan recall, menunjukkan cakupan rekomendasi dalam genre latin masih kecil.

- Diversity 16.67% menunjukkan variasi subgenre dalam rekomendasi lebih baik dibanding contoh genre rock sebelumnya, dengan 4 subgenre berbeda dari total 24 subgenre yang ada, menunjukkan rekomendasi lebih bervariasi.

**Kesimpulan**

Metode Content Based Filtering berhasil memberikan rekomendasi dengan presisi tinggi (100%) pada genre latin. Recall dan coverage masih rendah karena jumlah rekomendasi terbatas. Namun, tingkat diversity yang lebih tinggi menunjukkan sistem mampu menawarkan variasi subgenre yang lebih beragam, sehingga memberikan rekomendasi yang tidak hanya fokus pada satu atau dua subgenre saja.

### C. Evaluasi Hasil Rekomendasi Musik Berdasarkan Judul Lagu
**Deskripsi Dataset dan Evaluasi**

Dataset yang digunakan berisi total 1500 lagu dengan berbagai genre dan subkategori. Pada evaluasi ini, dilakukan pengujian dengan memasukkan input lagu Look What You Made Me Do (track_id: 1P17dC1amhFzptugyAO7Il) untuk menghasilkan rekomendasi sebanyak 10 lagu.

**Hasil Rekomendasi**

Dari hasil rekomendasi yang diberikan, seluruh lagu yang direkomendasikan (10 lagu) termasuk dalam genre pop, dengan seluruh subkategori yang sama yaitu post-teen pop.

| Metrik                                    | Nilai                                     | Keterangan                                                   |
| ----------------------------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| Jumlah rekomendasi                        | 10                                        | Total lagu yang direkomendasikan                             |
| Lagu rekomendasi genre "pop"              | 10                                        | Semua lagu rekomendasi bergenre pop                          |
| Lagu rekomendasi subgenre "post-teen pop" | 10                                        | Semua lagu subgenre post-teen pop                            |
| Presisi (Precision)                       | 10 / 10 = 1.00                            | Semua rekomendasi sesuai dengan genre input                  |
| Recall                                    | 10 / 230 = 0.0435 (4.35%)                 | Persentase lagu pop yang berhasil direkomendasikan           |
| Coverage                                  | (10 / 230) × 100 = 4.35%                  | Persentase cakupan lagu dalam genre pop dari total genre pop |
| Diversity                                 | 1 subgenre dari total 24 subgenre ≈ 4.17% | Variasi subgenre dalam rekomendasi dari total subgenre       |

**Interpretasi Hasil**

- Presisi 100% menunjukkan bahwa sistem hanya merekomendasikan lagu yang sangat relevan dengan genre input (pop), menunjukkan tingkat akurasi tinggi.

- Recall 4.35% relatif rendah karena sistem dibatasi hanya merekomendasikan 10 lagu dari total 230 lagu dalam genre pop.

- Coverage setara dengan recall karena dihitung dalam konteks genre tertentu, menandakan sistem hanya mencakup sebagian kecil dari semua lagu pop yang tersedia.

- Diversity rendah (4.17%) karena hanya ada satu subgenre yang muncul, yaitu post-teen pop. Ini menunjukkan sistem terlalu fokus pada satu jenis subgenre dan kurang memberikan variasi dalam rekomendasi.

**Kesimpulan**

Metode Content Based Filtering menghasilkan rekomendasi dengan presisi tinggi (100%) untuk lagu bergenre pop, khususnya subgenre post-teen pop. Namun, rendahnya nilai recall, coverage, dan diversity menunjukkan bahwa sistem masih dapat ditingkatkan dalam hal variasi dan cakupan rekomendasi, agar pengguna dapat menerima lebih banyak opsi yang tetap relevan namun lebih beragam dalam subgenre.
