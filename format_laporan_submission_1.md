# Laporan Proyek Machine Learning Prediksi Suhu Air Sungai Dengan Algoritma LSTM Unvariant dan Multivariant Single Forcasting - Mohammad Nurdin Prastya Hermansah

<div align="center">
<img src="https://github.com/user-attachments/assets/84becbde-88f0-4379-aa51-95d6fb6fc6e7" alt="" width="800"/>
<br/>
<strong>Gambar 1.</strong> Manfaat Air Untuk kehidupan
</div>

## Domain Proyek: Prediksi Suhu Air Menggunakan LSTM Unvariant dan Multivariat

### **Latar Belakang**

Suhu air merupakan salah satu parameter penting dalam berbagai sektor seperti perikanan, pengelolaan sumber daya air, pertanian, serta sistem pendinginan industri. Perubahan suhu air dapat mempengaruhi kualitas air, keberlangsungan ekosistem perairan, dan produktivitas kegiatan ekonomi berbasis air. Oleh karena itu, kemampuan untuk memprediksi suhu air secara akurat menjadi sangat krusial, khususnya dalam konteks perubahan iklim dan variabilitas cuaca ekstrem yang semakin meningkat.

Prediksi suhu air bukanlah tugas yang sederhana karena suhu dipengaruhi oleh banyak faktor eksternal seperti suhu udara, curah hujan, kelembaban, kecepatan angin, dan parameter lingkungan lainnya. Oleh karena itu, pendekatan prediktif yang mampu menangkap kompleksitas hubungan antar variabel sangat dibutuhkan. Salah satu metode yang kini banyak digunakan untuk menangani data deret waktu kompleks dan non-linear adalah Long Short-Term Memory (LSTM), sebuah arsitektur Recurrent Neural Network (RNN) yang dirancang untuk mengatasi masalah long-term dependencies dalam data time series.

### **Kenapa Masalah Ini Penting untuk Diselesaikan**

Dengan meningkatnya kebutuhan monitoring dan pengelolaan kualitas air secara proaktif, kemampuan untuk memprediksi suhu air dalam jangka pendek maupun menengah memiliki nilai praktis tinggi. Sebagai contoh:

* Dalam budidaya ikan, suhu air yang terlalu rendah atau tinggi dapat menyebabkan stres pada ikan dan menurunkan hasil panen.
* Dalam pembangkit listrik tenaga air atau sistem pendinginan industri, suhu air mempengaruhi efisiensi operasi.
* Dalam manajemen lingkungan, prediksi suhu dapat membantu mitigasi risiko terhadap gangguan ekosistem perairan.

Solusi berbasis machine learning, khususnya deep learning seperti LSTM, menawarkan pendekatan yang dapat meningkatkan akurasi prediksi dibandingkan metode konvensional (statistik klasik seperti ARIMA). Apalagi, dengan pendekatan **Unvariant dan Multivariat forecasting**.

### **Referensi Pendukung**

1. **Choubin, B., Khalighi-Sigaroodi, S., Malekian, A., & Sajedi-Hosseini, F. (2020).** "Prediction of water temperature using machine learning methods: application of random forest and support vector machine." *Journal of Hydrology*, 585, 124808.
   [https://doi.org/10.1016/j.jhydrol.2020.124808](https://doi.org/10.1016/j.jhydrol.2020.124808)

2. **Hu, H., Shu, L., & Zhang, Y. (2022).** "Deep learning-based water temperature forecasting: A comparison of LSTM, BiLSTM, and CNN-LSTM models." *Water*, 14(3), 317.
   [https://doi.org/10.3390/w14030317](https://doi.org/10.3390/w14030317)

3. **Hochreiter, S., & Schmidhuber, J. (1997).** "Long short-term memory." *Neural Computation*, 9(8), 1735–1780.
   [https://doi.org/10.1162/neco.1997.9.8.1735](https://doi.org/10.1162/neco.1997.9.8.1735)

## Business Understanding

### Problem Statements

Perubahan suhu air yang tidak terduga dapat berdampak negatif pada berbagai sektor, seperti perikanan, sistem pendinginan industri, dan manajemen kualitas lingkungan air. Instansi yang mengelola sumber daya air membutuhkan sistem prediksi suhu air yang akurat untuk mendukung pengambilan keputusan preventif dan efisien. Masalah utama yang dihadapi adalah bagaimana memprediksi suhu air secara akurat dalam beberapa langkah waktu ke depan dengan mempertimbangkan berbagai variabel lingkungan yang saling berkaitan.

### Goals

1. Membangun model prediktif berbasis machine learning/deep learning yang mampu:

2. Memprediksi suhu air untuk beberapa waktu ke depan secara akurat dengan dua metode yaitu unvariant dan multivariant.

3. Memanfaatkan lebih dari satu fitur (multivariat), seperti suhu udara, kelembaban, dan curah hujan, untuk meningkatkan akurasi.

5. Membandingkan efektivitas beberapa pendekatan atau algoritma dalam memecahkan masalah ini.
    - Mengevaluasi performa model menggunakan metrik kuantitatif seperti:
    - Mean Squared Error (MSE)
    - Root Mean Squared Error (RMSE)
    - Mean Absolute Error (MAE)
    - R² Score (koefisien determinasi)

### Solution statements

Untuk mencapai tujuan prediksi suhu air secara akurat dalam beberapa langkah ke depan, berikut adalah beberapa pendekatan solusi yang diajukan dan dapat diukur menggunakan metrik evaluasi kuantitatif:

#### Solusi 1: Univariate LSTM
1. Model LSTM dibangun menggunakan satu variabel input, yaitu suhu air historis.
2. Pendekatan ini berfungsi sebagai baseline untuk membandingkan apakah penggunaan satu fitur cukup efektif dalam memprediksi suhu air.
3. Metrik evaluasi: MSE, RMSE, MAE, dan R² Score.

#### Solusi 2: Multivariate LSTM
1. Menggunakan beberapa variabel input seperti WaterTemp (C), AirTemp (C), DissolvedOxygen (mg/L), Salinity (ppt),pH.
2. Tujuannya untuk melihat apakah penambahan fitur lingkungan dapat meningkatkan akurasi prediksi dibandingkan model univariate.
3. Metrik evaluasi: MSE, RMSE, MAE, dan R² Score.

#### Solusi 3: Hyperparameter Tuning untuk Optimasi Kinerja
1. Dilakukan tuning terhadap berbagai parameter model seperti:
2. Jumlah neuron (units) dalam lapisan LSTM
3. Jumlah layer tersembunyi
4. Learning rate
5. Panjang window (timesteps)
6. Ukuran batch
7. Epoch
8. Tuning dilakukan pada model univariate dan multivariate untuk mendapatkan performa terbaik.
9. Evaluasi hasil tuning dilakukan menggunakan metrik yang sama dan dibandingkan terhadap model sebelum tuning.

Pendekatan bertahap ini memungkinkan evaluasi menyeluruh, mulai dari baseline sederhana hingga model kompleks yang dioptimasi, sehingga solusi yang dihasilkan bersifat terukur, akurat, dan aplikatif dalam konteks prediksi suhu air.

## Data Understanding

### Sumber Data
Sumber dataset yang digunakan dalam proyek ini berasal dari Kaggle milik pengguna supriyoain dengan nama water_quality_data. Untuk melihat atau menggunakan dataset ini, silakan kunjungi tautan berikut: https://www.kaggle.com/datasets/supriyoain/water-quality-data.
Anda dapat menggunakan dataset ini tanpa perlu mengunduhnya ke komputer/laptop secara langsung, dengan mengikuti petunjuk akses data secara langsung seperti yang dijelaskan di bawah ini.
```python
# Upload file kaggel api
from google.colab import files
files.upload()

# set konfigurasi dan dwonload set
!mkdir -p ~/.kaggle
!cp kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json

# dwonload data
!kaggle datasets download -d supriyoain/water-quality-data

# ekstrak data
!unzip water-quality-data.zip
```
### Informasi Data

Dataset yang digunakan berisi 2371 baris dan 7 kolom yang merepresentasikan kualitas air, dengan fitur-fitur sebagai berikut:
- Date: Tanggal pengukuran
- Salinity (ppt): Tingkat salinitas air
- Dissolved Oxygen (mg/L): Oksigen terlarut
- pH: Tingkat keasaman air
- Secchi Depth (m): Kedalaman visibilitas (kejernihan air)
- Water Depth (m): Kedalaman air
- Water Temp (°C): Suhu air
- Air Temp (°C): Suhu udara

### Eksplorasi Data & Visualisasi Data

Beberapa langkah Exploratory Data Analysis (EDA) telah dilakukan untuk memahami distribusi serta hubungan antar fitur dalam dataset. Di bawah ini merupakan ringkasan dari beberapa tahapan EDA yang telah dilakukan. 

#### Data Wrangling
##### 1. Download Data
Gunakan kode di bawah ini untuk download dataset dari Kaggle dengan Kaggle API.

```python
# Upload file kaggle api
from google.colab import files
files.upload()
    
# Set konfigurasi dan download set
!mkdir -p ~/.kaggle
!cp kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json
    
# Download data
!kaggle datasets download -d supriyoain/water-quality-data
    
# Ekstrak data
!unzip water-quality-data.zip
```

---

##### 2. Data Akuisisi
Gunakan kode di bawah ini untuk akuisisi data dengan pandas.

```python
# Ambil data
import pandas as pd
data = pd.read_csv("waterquality.csv")

# Baca dataset
data.head()
```

---

##### 3. Data Assessing
Gunakan kode di bawah ini untuk cek data apakah ada missing value dan duplicated data.

```python
# Cek info data
data.info()

# Cek missing value
data.isna().sum()

# Cek duplikasi data
print('duplikasi data: ', data.duplicated().sum())
```

---

##### 4. Data Cleaning
Gunakan kode untuk cleaning data missing value dan juga konversi data. Metode interpolasi dipilih karena cocok untuk time series data sensor.

```python
# Mengatasi missing value dengan interpolate
data['Salinity (ppt)'] = data['Salinity (ppt)'].interpolate(method='linear')
data['DissolvedOxygen (mg/L)'] = data['DissolvedOxygen (mg/L)'].interpolate(method='linear')
data['pH'] = data['pH'].interpolate(method='linear')
data['SecchiDepth (m)'] = data['SecchiDepth (m)'].interpolate(method='linear')
data['WaterDepth (m)'] = data['WaterDepth (m)'].interpolate(method='linear')
data['WaterTemp (C)'] = data['WaterTemp (C)'].interpolate(method='linear')

# Fill forward/backward setelah interpolate
data['Salinity (ppt)'] = data['Salinity (ppt)'].fillna(method='ffill').fillna(method='bfill')
data['DissolvedOxygen (mg/L)'] = data['DissolvedOxygen (mg/L)'].fillna(method='ffill').fillna(method='bfill')

# Mengatasi missing value pada kolom Date
print(data['Date'].isna().sum())     # berapa banyak missing
print(data['Date'].head(10))         # contoh data awal
print(data[data['Date'].isna()])     # lihat baris yang missing Date

data['Date'] = data['Date'].fillna(method='ffill')
```


#### Exploratory Data Analisis

Tahap eksplorasi data ini bertujuan untuk memahami struktur, karakteristik, serta pola yang terkandung dalam dataset sebelum dilakukan proses analisis lanjutan atau pemodelan. Dengan melakukan eksplorasi data, kita dapat mengidentifikasi berbagai hal penting seperti jumlah data, tipe data pada masing-masing kolom, nilai yang hilang, distribusi nilai, serta hubungan antar variabel. Proses ini juga membantu dalam menemukan potensi outlier, tren musiman, atau pola waktu tertentu yang dapat memengaruhi hasil analisis. Selain itu, eksplorasi data sangat penting untuk memastikan kualitas data yang digunakan sudah memadai dan sesuai dengan tujuan analisis, sehingga proses selanjutnya dapat dilakukan secara lebih akurat dan efisien. Beberapa langkah yang dilakukan meliputi:
##### 1. Menampilkan Informasi Umum Dataset  
Proses ini digunakan untuk memahami struktur dataset, jumlah baris, tipe data tiap kolom, dan statistik dasar seperti rata-rata, nilai maksimum, minimum, dll.

```python
# Jumlah data
print(len(data))

# Cek info data
data.info()

# Deskripsi statistik
data.describe()
```

---

##### 2. Menampilkan Histogram Distribusi Data  
Digunakan untuk melihat distribusi nilai dari setiap fitur numerik dalam dataset. Membantu memahami apakah data normal, skewed, atau memiliki outlier.

```python
# Menampilkan histogram distribusi data untuk semua kolom numerik
data.select_dtypes(include='number').hist(figsize=(12, 8), bins=30, edgecolor='black')
```

---

##### 3. Mengubah Kolom Date Menjadi Tipe Datetime dan Mengatur sebagai Index  
Langkah ini penting untuk analisis time series. Dengan menjadikan kolom `Date` sebagai indeks, kita bisa melakukan resampling dan visualisasi berdasarkan waktu.

```python
# Ubah Kolom Date jadi datetime dan set sebagai index
data['Date'] = pd.to_datetime(data['Date'])
data.set_index('Date', inplace=True)
data = data.sort_index()  # pastikan urut waktu
```

---

##### 4. Menampilkan Plot Tren Time Series  
Visualisasi seluruh parameter sensor terhadap waktu. Membantu mengamati pola umum, tren, atau anomali dalam data seiring waktu.

```python
# Plot tren waktu time series
import matplotlib.pyplot as plt

data.plot(subplots=True, figsize=(12, 10), title='Time Series of Sensor Data')
plt.tight_layout()
plt.show()
```

---

##### 5. Membuat Matriks Korelasi antar Variabel  
Digunakan untuk mengukur hubungan antar fitur numerik, apakah dua fitur memiliki korelasi positif, negatif, atau tidak berkorelasi.

```python
# Matriks korelasi variabel
import seaborn as sns
import matplotlib.pyplot as plt

plt.figure(figsize=(8,6))
sns.heatmap(data.corr(), annot=True, cmap='coolwarm')
plt.title("Correlation Matrix")
plt.show()
```

---

##### 6. Menampilkan Pola Musiman (Bulanan)  
Dengan resampling bulanan, kita bisa melihat apakah terdapat pola musiman atau tren jangka panjang dalam data, seperti kenaikan suhu di musim panas.

```python
# Musiman atau Pola Harian/Bulanan
data_monthly = data.resample('M').mean()
data_monthly.plot(figsize=(12, 6), title='Monthly Average of Parameters')
plt.show()
```

---

##### 7. Visualisasi Gabungan Distribusi dan Korelasi (Pairplot)  
`pairplot` membantu melihat hubungan dan sebaran antar semua kombinasi fitur numerik. Ini sangat berguna untuk eksplorasi awal data.

```python
# Visualisasi gabungan distribusi dan korelasi
import seaborn as sns
import matplotlib.pyplot as plt

sns.pairplot(data.sample(500))  # sampling untuk mempercepat plotting
plt.show()
```

##### Kesimpulan EDA

| Aspek               | Intisari Utama                                                                                                                                                                                                            |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Distribusi Data** | Kebanyakan variabel (Salinity, Secchi Depth, Water Depth, pH) miring ke kanan, data terkonsentrasi di nilai rendah (air tawar, dangkal, air keruh, pH netral). Water Temp bimodal, Air Temp miring kanan.                 |
| **Pola Waktu**      | Pola musiman kuat pada suhu air & udara, serta Dissolved Oxygen yang berfluktuasi mengikuti suhu. Variabel lain relatif stabil, ada celah data dan outlier (pH rendah, suhu ekstrem).                                     |
| **Korelasi**        | Secchi Depth & Water Depth sangat kuat positif (r=0.81). Water Temp & Air Temp positif (r=0.68). Dissolved Oxygen negatif signifikan terhadap Water Temp (r=-0.54) dan Air Temp (r=-0.34). Variabel lain korelasi rendah. |
| **Catatan Penting** | Data outlier pada pH dan suhu perlu dicek ulang. Banyak data menggambarkan kondisi lingkungan dangkal, keruh, dan salinitas rendah dengan pengaruh kuat musim terhadap suhu dan oksigen.                                  |


## Data Preparation
Tahap data preparation (persiapan data) merupakan proses penting dalam analisis data dan pemodelan, karena memastikan bahwa data dalam kondisi bersih, konsisten, dan siap digunakan untuk pelatihan model. Pada tahap ini, dilakukan beberapa langkah utama:

1. Deteksi dan penanganan outlier
2. Normalisasi fitur numerik
   
Kedua langkah ini bertujuan untuk meningkatkan kualitas data agar hasil analisis dan prediksi dari model lebih akurat dan tidak bias terhadap nilai ekstrem atau perbedaan skala antar variabel.

### Cek outlier
Langkah pertama adalah mengidentifikasi outlier menggunakan boxplot, yang secara visual memperlihatkan nilai-nilai ekstrem di luar rentang normal (di luar whisker dari boxplot). Ini dilakukan untuk setiap kolom numerik.
```python
# Pilih hanya kolom dengan tipe data numerik
numeric_columns = data.select_dtypes(include=['number']).columns

# Plot boxplot hanya untuk kolom numerik
for feature in numeric_columns:
    plt.figure(figsize=(10, 5))
    plt.boxplot(x=data[feature])
    plt.title(f"Box Plot Of {feature}")
    plt.show()
```

<div align="center">
<img width="776" alt="image" src="https://github.com/user-attachments/assets/b805d646-2876-4784-ad6c-d4239ba04277" />
<br/>
<strong>Gambar 2.</strong> Hasil Cek Outlier
</div>

### Tangani Outlier Metode IQR
Setelah outlier terdeteksi, digunakan metode Interquartile Range (IQR) untuk menentukan batas bawah dan atas dari nilai normal. Outlier kemudian digantikan dengan nilai median dari kolom tersebut. Metode ini dipilih karena median tidak terpengaruh oleh nilai ekstrem dan mampu mempertahankan distribusi alami data.
```pyhton
# Tangani outlier

# Pilih hanya kolom dengan tipe data numerik
numeric_columns = data.select_dtypes(include=['number']).columns

# Tangani outlier dengan mengganti dengan median atau mean
for feature in numeric_columns:
    Q1 = data[feature].quantile(0.25)
    Q3 = data[feature].quantile(0.75)
    IQR = Q3 - Q1
    lower_bound = Q1 - 1.5 * IQR
    upper_bound = Q3 + 1.5 * IQR

    # Buat mask untuk outlier
    outliers = (data[feature] < lower_bound) | (data[feature] > upper_bound)

    # Ganti outlier dengan median (atau bisa ganti jadi df[feature].mean())
    median_value = data[feature].median()
    data.loc[outliers, feature] = median_value
```
<div align="center">
<img width="786" alt="image" src="https://github.com/user-attachments/assets/ead1ae5d-0415-4c58-8635-c4cc88801f6f" />
<br/>
<strong>Gambar 3.</strong> Hasil Penanganan Outlier Dengan Median
</div>

### Normalisasi Data
Setelah menangani outlier, dilakukan normalisasi data agar semua fitur numerik berada dalam skala yang seragam, umumnya antara 0 dan 1. Proses ini penting karena algoritma machine learning seperti KNN, SVM, atau Neural Networks sensitif terhadap perbedaan skala. Jika tidak dinormalisasi, fitur dengan rentang nilai besar akan mendominasi model dan menghasilkan prediksi yang bias.

<div align="center">
<img width="301" alt="image" src="https://github.com/user-attachments/assets/0e392499-4062-43ab-bd61-f74433d84294" />
<br/>
<strong>Gambar 4.</strong> Sebelum Normalisasi Data
</div>

```python
from sklearn.preprocessing import MinMaxScaler

# Inisialisasi MinMaxScaler
scaler = MinMaxScaler()

# Copy data asli
data_scaled = data_filter.copy()

# Pilih hanya kolom numerik
numerical_cols = data_filter.select_dtypes(include=['number']).columns

# Normalisasi kolom numerik
data_scaled[numerical_cols] = scaler.fit_transform(data_filter[numerical_cols])

# Tampilkan hasil
data_scaled.describe()
```

<div align="center">
<img width="305" alt="image" src="https://github.com/user-attachments/assets/7a542843-80f8-496a-b8ad-5dc20f159f6b" />
<br/>
<strong>Gambar 5.</strong> Setelah Normalisasi Data
</div>


## Modeling
Pada tahap *modeling*, saya menggunakan algoritma **Long Short-Term Memory (LSTM)** untuk memprediksi **suhu air (Water Temperature)** berdasarkan data deret waktu (*time series*). Pemilihan LSTM didasarkan pada kemampuannya dalam menangkap pola dan ketergantungan jangka panjang pada data berurutan, yang sangat sesuai untuk data sensor lingkungan.

### Pendekatan yang Digunakan

Saya melakukan dua pendekatan dalam pemodelan:

#### 1. **Univariate Single Forecasting**

* Model ini hanya menggunakan **suhu air (Water Temp)** sebagai fitur input untuk memprediksi suhu air pada waktu berikutnya.
* Tujuan pendekatan ini adalah melihat seberapa baik suhu masa lalu dapat memprediksi suhu masa depan tanpa bantuan variabel lain.

#### 2. **Multivariate Single Forecasting**

* Model ini menggunakan beberapa fitur sekaligus (misalnya: suhu udara, salinitas, DO, kedalaman, dll.) untuk memprediksi suhu air.
* Pendekatan ini bertujuan menangkap pengaruh variabel lingkungan lain terhadap suhu air, sehingga prediksi menjadi lebih akurat.

### Proses Tuning Hyperparameter

Untuk kedua pendekatan, dilakukan proses **hyperparameter tuning** guna menemukan kombinasi parameter terbaik. Parameter yang dioptimalkan antara lain:

* Jumlah neuron di hidden layer
* Panjang *time window* (lag)
* Jumlah *epochs* dan ukuran *batch*
* Fungsi aktivasi, optimizer (misal Adam), dan dropout

### Evaluasi Model

Evaluasi dilakukan dengan dua metrik utama:

* **R-squared (R²)**: Mengukur seberapa baik prediksi mengikuti variasi data aktual. Target minimal ditetapkan sebesar **50%**, namun hasilnya **jauh melampaui** target tersebut.
* **Error (RMSE/MAE)**: Digunakan untuk mengukur rata-rata kesalahan prediksi.

### Hasil Akhir

* Kedua pendekatan (univariate dan multivariate) berhasil mencapai nilai **R² antara 85% hingga 86%**, menunjukkan bahwa model mampu menangkap pola dengan sangat baik.
* Nilai error (MAE dan RMSE) juga **relatif kecil**, yang berarti deviasi antara nilai prediksi dan aktual rendah.

> **Kesimpulan:**
> Baik pendekatan univariate maupun multivariate sama-sama memberikan hasil yang sangat baik, namun pendekatan **multivariate memberikan keunggulan tambahan** karena mempertimbangkan hubungan antar fitur lingkungan.




## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.

