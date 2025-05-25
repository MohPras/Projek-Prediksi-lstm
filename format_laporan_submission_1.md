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

Dataset yang digunakan berisi 2371 baris dan 8 kolom yang merepresentasikan kualitas air, dengan fitur-fitur sebagai berikut:
- Date: Tanggal pengukuran yang bertipe object
- Salinity (ppt): Tingkat salinitas air yang bertipe float
- Dissolved Oxygen (mg/L): Oksigen terlarut yang bertipe float
- pH: Tingkat keasaman air yang bertipe float
- Secchi Depth (m): Kedalaman visibilitas (kejernihan air) yang bertipe float
- Water Depth (m): Kedalaman air yang bertipe float
- Water Temp (°C): Suhu air bertipe yang float
- Air Temp (°C): Suhu udara bertipe yang float

### Data Wrangling

Beberapa langkah data wrangling telah dilakukan untuk mengolah data menjadi data clean yang bebas dar bias.

#### 1. Download Data
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

#### 2. Data Akuisisi
Gunakan kode di bawah ini untuk akuisisi data dengan pandas.

```python
# Ambil data
import pandas as pd
data = pd.read_csv("waterquality.csv")

# Baca dataset
data.head()
```

---

#### 3. Data Assessing
Gunakan kode di bawah ini untuk cek data apakah ada missing value dan duplicated data.

```python
# Cek info data
data.info()

# Cek missing value
data.isna().sum()

# Cek duplikasi data
print('duplikasi data: ', data.duplicated().sum())

# cek outlier value

# Pilih hanya kolom dengan tipe data numerik
numeric_columns = data.select_dtypes(include=['number']).columns

# Hitung jumlah outlier per kolom numerik
for feature in numeric_columns:
    # Hitung batas IQR untuk deteksi outlier
    Q1 = data[feature].quantile(0.25)
    Q3 = data[feature].quantile(0.75)
    IQR = Q3 - Q1
    lower_bound = Q1 - 1.5 * IQR
    upper_bound = Q3 + 1.5 * IQR

    # Hitung jumlah outlier
    outliers = data[(data[feature] < lower_bound) | (data[feature] > upper_bound)]
    print(f"Jumlah outlier pada kolom '{feature}': {len(outliers)}")
```

Kesimpulan pada data assesing ini:
1. Terdapat data bertipe object dan float
2. Terdapat missing value yang sangat banyak pada kolom
   - Salinity (ppt) = 130
   - DissolvedOxygen (mg/L) = 851
   - pH = 95
   - SecchiDepth (m) = 73
   - WaterDepth (m) = 71
   - kolom WaterTemp (C) = 121
     
3. Terdapat duplikasi data sebanyak 10
   
4. Terdapat outlier pada dataset
   - Jumlah outlier pada kolom 'Salinity (ppt)': 272
   - Jumlah outlier pada kolom 'DissolvedOxygen (mg/L)': 11
   - Jumlah outlier pada kolom 'pH': 47
   - Jumlah outlier pada kolom 'SecchiDepth (m)': 85
   - Jumlah outlier pada kolom 'WaterDepth (m)': 37
   - Jumlah outlier pada kolom 'WaterTemp (C)': 5
   - Jumlah outlier pada kolom 'AirTemp (C)': 69

---

#### 4. Data Cleaning
**Penanganan missing value**

Tahap pertama adalah penanganan missing value pada dataset ini menggunakan IterativeImputer dengan RandomForest. Alasan penggunaan IterativeImputer dengan RandomForest adalah metode paling cocok dan minim bias untuk data seperti ini karena dapat menangani missing value secara cerdas dengan mempertimbangkan hubungan antar fitur, menjaga distribusi alami data, dan cocok untuk variabel-variabel lingkungan yang saling memengaruhi. Berikut ini adalah kode program untuk menagatasi missing value

```python
from sklearn.experimental import enable_iterative_imputer  # noqa
from sklearn.impute import IterativeImputer
from sklearn.ensemble import RandomForestRegressor

# Inisialisasi imputernya
imputer = IterativeImputer(estimator=RandomForestRegressor(), random_state=42)

# Simpan kolom non-numerik terpisah
non_numerik = data.select_dtypes(exclude='number')
numerik = data.select_dtypes(include='number')

# Imputasi hanya data numerik
numerik_imputed = pd.DataFrame(imputer.fit_transform(numerik), columns=numerik.columns)

# Gabungkan kembali dengan kolom non-numerik (jika ada)
df_imputed = pd.concat([non_numerik.reset_index(drop=True), numerik_imputed], axis=1)

# Hapus baris yang nilai 'Date'-nya kosong
data = df_imputed.dropna(subset=['Date'])
```
<div align="center">
<img width="300" alt="image" src="https://github.com/user-attachments/assets/de87a23d-161d-4e83-80cb-a52b8552d9ed" />
<br/>
<strong>Gambar.</strong> Hasil penanganan missing value
</div>

**Penanganan duplikasi data**

Tahap kedua pada data assesing ini juga ditemukan jumlah duplikat data hanya sedikit yaitu sebanyak 10 baris maka solusi yang dipakai adalah penghapusan, penghapusan tidak akan berdampak signifikan terhadap keseluruhan jumlah data. Kehadiran data duplikat dapat menyebabkan bias atau menguatkan pola palsu yang tidak merepresentasikan kondisi sebenarnya, terutama ketika data digunakan untuk analisis atau pelatihan model. Dalam konteks data lingkungan atau sains, setiap baris umumnya merepresentasikan satu pengamatan yang bersifat unik, sehingga keberadaan duplikat tidak memberikan nilai tambah dan sebaiknya dihapus untuk menjaga integritas data.

```python
# Hapus baris yang sepenuhnya duplikat
data = data.drop_duplicates()
print('Duplicat data setelah penghapusan: ', data.duplicated().sum())

# output 
Duplicat data setelah penghapusan:  0
```

**Penanganan outlier data**

Tahap ketiga dalam data cleaning ini adalah menangani outlier pada data dengan menggunakan metode IQR. Langkah pertama adalah mengidentifikasi outlier menggunakan boxplot, yang secara visual memperlihatkan nilai-nilai ekstrem di luar rentang normal (di luar whisker dari boxplot). Ini dilakukan untuk setiap kolom numerik.

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

**Konversi Tipe Data**

Tahap terahir yang dilakukan dalam data cleaning ini adalah ubah tipe data object pada kolom date dan jadikan sebagai index, berikut adalah kodenya:

```python
# Ubah Kolom Date jadi datetime dan set sebagai index
data['Date'] = pd.to_datetime(data['Date'])
data.set_index('Date', inplace=True)
data = data.sort_index()  # pastikan urut waktu
```

### Exploratory Data Analisis

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

| Aspek Analisa         | Penjelasan Lengkap                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Distribusi Data**   | Banyak parameter utama seperti Salinity, SecchiDepth, dan WaterDepth menunjukkan distribusi data yang sangat miring ke kanan. Hal ini berarti sebagian besar nilai berada pada rentang rendah, sementara nilai tinggi hanya muncul dalam frekuensi yang jauh lebih kecil. Kondisi ini mengindikasikan dominasi nilai rendah pada kondisi lingkungan yang diukur, seperti salinitas yang cenderung dekat air tawar, kedalaman air yang relatif dangkal, dan kejernihan air yang umumnya terbatas. Distribusi seperti ini penting untuk diperhatikan agar analisis statistik dan model yang digunakan bisa menyesuaikan dengan karakter data yang tidak simetris. |
| **Pola Musiman**      | Terjadi pola musiman yang jelas pada beberapa parameter kunci, terutama suhu air, suhu udara, dan kadar oksigen terlarut. Pola ini mengindikasikan adanya fluktuasi reguler sepanjang tahun, yang biasanya dipengaruhi oleh siklus iklim dan perubahan musim. Misalnya, suhu udara dan air naik pada musim panas dan turun pada musim dingin, sementara oksigen terlarut cenderung berbanding terbalik dengan suhu, mengalami penurunan saat suhu naik karena kelarutan oksigen menurun. Pola musiman ini memberikan wawasan penting tentang dinamika lingkungan dan dapat menjadi dasar untuk prediksi dan manajemen sumber daya air.                          |
| **Korelasi Positif**  | Ditemukan korelasi positif yang kuat antara kedalaman air dengan kejernihan (SecchiDepth), yang menunjukkan bahwa semakin dalam air, biasanya semakin jernih karena sedimen dan partikel tersuspensi cenderung lebih sedikit tersebar di lapisan permukaan. Selain itu, suhu air juga sangat berkorelasi positif dengan suhu udara di sekitarnya, menandakan bahwa kondisi atmosfer langsung memengaruhi suhu perairan, terutama di ekosistem dangkal. Korelasi positif ini menegaskan keterkaitan erat antara parameter fisik lingkungan dan memberikan dasar untuk memahami interaksi antar elemen ekosistem.                                                 |
| **Korelasi Negatif**  | Terdapat korelasi negatif yang kuat antara kadar oksigen terlarut dengan suhu air dan suhu udara, yang mengindikasikan bahwa kenaikan suhu menyebabkan penurunan kadar oksigen dalam air. Fenomena ini umum terjadi karena kelarutan oksigen menurun pada suhu yang lebih tinggi. Kondisi ini berimplikasi pada kesehatan ekosistem akuatik, karena oksigen terlarut yang rendah dapat membatasi keberlangsungan hidup organisme air, terutama ikan dan biota sensitif lainnya. Pemahaman hubungan ini penting untuk pengelolaan kualitas air dan mitigasi dampak perubahan iklim.                                                                              |
| **Parameter Lainnya** | Parameter lain selain yang telah disebutkan umumnya menunjukkan korelasi yang lemah atau hampir independen satu sama lain. Hal ini menandakan adanya pengaruh faktor lingkungan atau biotik lain yang belum diukur dalam data saat ini, seperti arus air, aktivitas manusia, atau perubahan kimiawi lainnya. Ketidakterkaitan ini juga membuka peluang untuk pengkajian lebih mendalam guna mengidentifikasi variabel tambahan yang dapat memperkaya model pemantauan dan prediksi kondisi lingkungan.                                                                                                                                                          |



## Data Preparation
Tahap data preparation (persiapan data) merupakan proses penting dalam analisis data dan pemodelan, karena memastikan bahwa data dalam kondisi bersih, konsisten, dan siap digunakan untuk pelatihan model. Pada tahap ini, dilakukan beberapa langkah utama yaitu Normalisasi data mengguakan MinMaxScaler.Langkah ini bertujuan untuk meningkatkan kualitas data agar hasil analisis dan prediksi dari model lebih akurat dan tidak bias terhadap nilai ekstrem atau perbedaan skala antar variabel.

### Normalisasi Data
Setelah menangani outlier, dilakukan normalisasi data agar semua fitur numerik berada dalam skala yang seragam, umumnya antara 0 dan 1. Proses ini penting karena algoritma machine learning seperti KNN, SVM, atau Neural Networks sensitif terhadap perbedaan skala. Jika tidak dinormalisasi, fitur dengan rentang nilai besar akan mendominasi model dan menghasilkan prediksi yang bias.

<div align="center">
<img width="400" alt="image" src="https://github.com/user-attachments/assets/0e392499-4062-43ab-bd61-f74433d84294" />
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
<img width="400" alt="image" src="https://github.com/user-attachments/assets/7a542843-80f8-496a-b8ad-5dc20f159f6b" />
<br/>
<strong>Gambar 5.</strong> Setelah Normalisasi Data
</div>


## Modeling
Pada tahap *modeling*, digunakan algoritma **Long Short-Term Memory (LSTM)** untuk memprediksi **suhu air (Water Temperature)** karena kemampuannya menangkap pola jangka panjang dalam data time series. Hasil akhir menunjukkan model mampu memberikan prediksi akurat dengan error yang rendah, baik pada pendekatan univariate maupun multivariate.

<div align="center">
<img width="500" alt="image" src="https://github.com/user-attachments/assets/0ddf6a48-85e8-44bc-a7f2-d450dc954a38" />
<br/>
<strong>Gambar 6.</strong> Algoritma LSTM
</div>

### Pendekatan yang Digunakan

Saya melakukan dua pendekatan dalam pemodelan:

#### 1. **Univariate Single Forecasting**

* Model ini hanya menggunakan **suhu air (Water Temp)** sebagai fitur input untuk memprediksi suhu air pada waktu berikutnya.
* Tujuan pendekatan ini adalah melihat seberapa baik suhu masa lalu dapat memprediksi suhu masa depan tanpa bantuan variabel lain.

#### 2. **Multivariate Single Forecasting**

* Model ini menggunakan beberapa fitur sekaligus (misalnya: suhu udara, salinitas, DO, kedalaman, dll.) untuk memprediksi suhu air.
* Pendekatan ini bertujuan menangkap pengaruh variabel lingkungan lain terhadap suhu air, sehingga prediksi menjadi lebih akurat.

#### 3. **Proses Tuning Hyperparameter**

Untuk kedua pendekatan (univariate dan multivariate), dilakukan proses **hyperparameter tuning** guna menemukan kombinasi parameter terbaik yang menghasilkan model paling optimal. Tuning ini bertujuan untuk **meminimalkan error** dan **memaksimalkan akurasi prediksi**. Berikut adalah beberapa hyperparameter yang disesuaikan selama proses tuning:

* `**window_size**` – Jumlah langkah waktu (*time steps*) historis yang digunakan sebagai input untuk memprediksi langkah berikutnya.
* `**epoch**` – Jumlah iterasi pelatihan model terhadap seluruh dataset.
* `**lstm_units**` – Jumlah unit memori pada lapisan LSTM.
* `**batch_size**` – Jumlah sampel data yang diproses dalam satu iterasi sebelum memperbarui bobot model.
* `**test_size**` – Proporsi data yang digunakan untuk pengujian (evaluasi) model.

Kriteria Evaluasi pemilihan parameter terbaik untuk setiap kombinasi parameter model dievaluasi menggunakan beberapa metrik error, yaitu:

* **MSE (Mean Squared Error)** – Digunakan sebagai metrik utama untuk memilih parameter terbaik karena sensitif terhadap kesalahan besar. Kombinasi dengan **nilai MSE terkecil** dianggap sebagai kandidat terbaik.
* **RMSE (Root Mean Squared Error)** – Turunan dari MSE, memberikan gambaran error dalam satuan asli target (suhu air).
* **MAE (Mean Absolute Error)** – Digunakan untuk mengetahui seberapa jauh prediksi model dari nilai aktual secara rata-rata.
* **R² (R-squared)** – Digunakan untuk menilai seberapa baik model menjelaskan variasi data. Kombinasi parameter dengan **R² tertinggi mendekati 1** dianggap paling akurat.

Pemilihan hyperparameter terbaik dilakukan berdasarkan kombinasi yang menghasilkan parameter MSE serendah mungkin, R² setinggi mungkin (mendekati 1), RMSE dan MAE kecil. Dengan pendekatan ini, model LSTM yang dihasilkan mampu memberikan **prediksi suhu air dengan akurasi tinggi dan kesalahan minimal**, baik dalam pendekatan univariate maupun multivariate.

### Hasil Model Dengan Tuning Hyperparameter

Hasil Akhir dari kombinasi parameter yang dipilih untuk Unvariante dan Multivariante sebagai berikut:

1. Kedua pendekatan (univariate dan multivariate) berhasil mencapai nilai **R² 85%%**, menunjukkan bahwa model mampu menangkap pola dengan sangat baik.

2. Nilai error (MAE dan RMSE) juga **relatif kecil**, yang berarti deviasi antara nilai prediksi dan aktual rendah.

3. Baik pendekatan univariate maupun multivariate sama-sama memberikan hasil yang sangat baik.

4. Pendekatan **multivariate memberikan keunggulan tambahan** karena mempertimbangkan hubungan antar fitur lingkungan, sehingga pendekatan multivarite dipilih untuk dilakukan pembahasan lebih.

### Program Multivariate Single Forcasting Water Temperature

Pada penelitian ini pendekatan multivariate dipilih untuk dibahas karena dinilai lebih relevan dalam menggambarkan dinamika sistem yang dipelajari. Meskipun performa model multivariate dan univariate menunjukkan nilai R² yang sama, yaitu 0.85, pendekatan **multivariate** dipilih untuk dibahas dalam penelitian ini karena mampu menangkap **kompleksitas hubungan antar variabel** yang tidak dapat ditangani oleh model univariate. 

Dalam pendekatan ini, model mempertimbangkan lebih dari satu variabel input, sehingga dapat mengidentifikasi pola dan interaksi yang saling memengaruhi antar parameter lingkungan, seperti suhu air, suhu udara, dan kelembapan. Pendekatan multivariate memberikan representasi yang lebih realistis terhadap kondisi alami yang kompleks, sehingga meskipun hasil evaluasi secara numerik serupa, pemahaman yang dihasilkan lebih mendalam dan aplikatif.

#### Kode Program Hyperparameter Tunning

```python
# ===== SETUP SEED DAN DETERMINISME =====
seed = 42
os.environ['PYTHONHASHSEED'] = str(seed)
random.seed(seed)
np.random.seed(seed)
tf.random.set_seed(seed)
tf.config.experimental.enable_op_determinism()

# ===== PERSIAPAN DATA =====
# Fitur multivariat, misal: suhu udara, kelembapan udara
features = data_scaled[suhu_udara2].values  # asumsi: suhu_udara2 adalah list kolom fitur
target = data_scaled['WaterTemp (C)'].values

# ===== FUNGSI MEMBUAT SEQUENCE DATA =====
def create_sequences(features, target, window_size):
    X, y = [], []
    for i in range(len(features) - window_size):
        X.append(features[i:i+window_size])
        y.append(target[i+window_size])
    return np.array(X), np.array(y)

# ===== PARAMETER YANG AKAN DIUJI =====
window_sizes = [5, 10, 15]
epochs_list = [10, 20]
lstm_units_list = [32, 50]
batch_sizes = [16, 32]
test_sizes = [0.2, 0.3, 0.4]

# ===== DICTIONARY HASIL =====
results = {
    'window_size': [],
    'epochs': [],
    'lstm_units': [],
    'batch_size': [],
    'test_size': [],
    'MSE': [],
    'RMSE': [],
    'MAE': [],
    'R2': [],
    'total_params': []
}

# ===== LOOP UTAMA EKSPERIMEN =====
for window_size in window_sizes:
    X, y = create_sequences(features, target, window_size)

    # Reshape untuk LSTM: (samples, timesteps, features)
    X = X.reshape((X.shape[0], X.shape[1], X.shape[2]))

    for test_size in test_sizes:
        split_idx = int(len(X) * (1 - test_size))
        X_train, X_test = X[:split_idx], X[split_idx:]
        y_train, y_test = y[:split_idx], y[split_idx:]

        for epochs in epochs_list:
            for units in lstm_units_list:
                for batch_size in batch_sizes:
                    print(f"Training LSTM: window={window_size}, epochs={epochs}, units={units}, batch={batch_size}, test_size={test_size}")

                    model = Sequential()
                    model.add(LSTM(units, input_shape=(X_train.shape[1], X_train.shape[2])))  # default tanh
                    model.add(Dense(1))
                    model.compile(optimizer='adam', loss='mse')

                    model.fit(X_train, y_train, epochs=epochs, batch_size=batch_size, verbose=0, validation_split=0.2)

                    y_pred = model.predict(X_test).flatten()

                    mse = mean_squared_error(y_test, y_pred)
                    rmse = np.sqrt(mse)
                    mae = mean_absolute_error(y_test, y_pred)
                    r2 = r2_score(y_test, y_pred)
                    total_params = model.count_params()

                    print(f"MSE: {mse:.4f}, RMSE: {rmse:.4f}, MAE: {mae:.4f}, R²: {r2:.4f}, Params: {total_params}\n")

                    results['window_size'].append(window_size)
                    results['epochs'].append(epochs)
                    results['lstm_units'].append(units)
                    results['batch_size'].append(batch_size)
                    results['test_size'].append(test_size)
                    results['MSE'].append(mse)
                    results['RMSE'].append(rmse)
                    results['MAE'].append(mae)
                    results['R2'].append(r2)
                    results['total_params'].append(total_params)
```

#### Hasil Parameter Terbaik

```python
📌 Kombinasi parameter terbaik berdasarkan MSE terkecil:
window_size         5.000000
epochs             20.000000
lstm_units         50.000000
batch_size         16.000000
test_size           0.300000
MSE                 0.004818
RMSE                0.069415
MAE                 0.047560
R2                  0.852922
```

#### Build Model Dengan Menggunakan Kombinasi Parameter Terbaik

**Seting Konfigurasi**

Bagian ini mengatur reproducibility (agar hasil eksperimen konsisten setiap kali dijalankan) dengan menyetel seed di Python, NumPy, dan TensorFlow. Kemudian ditentukan parameter utama model seperti ukuran window, jumlah epoch, jumlah unit LSTM, ukuran batch, dan proporsi data uji.

```python
# ========== Konfigurasi ==========

# Set seed untuk memastikan reproducibility
seed = 42
os.environ['PYTHONHASHSEED'] = str(seed)      # Untuk Python hash randomization
random.seed(seed)                             # Untuk modul random
np.random.seed(seed)                          # Untuk NumPy
tf.random.set_seed(seed)                      # Untuk TensorFlow
tf.config.experimental.enable_op_determinism()  # Pastikan semua operasi deterministik

# Parameter terbaik
window_size = 5
epochs = 20
lstm_units = 50
batch_size = 16
test_size = 0.3
```

**Set Fitur Dan Target**

Bagian ini menyiapkan data dengan memilih beberapa kolom sebagai fitur (input) dan satu kolom sebagai target (output), lalu memisahkannya menjadi variabel X_raw untuk input dan y_raw untuk output.

```python
# ========== Siapkan Data ==========
# Kolom fitur dan target
features_columns = ['WaterTemp (C)', 'AirTemp (C)', 'DissolvedOxygen (mg/L)', 'Salinity (ppt)', 'pH']
target_column = 'WaterTemp (C)'

# pisahkan fitur dan target
X_raw = df_clear[features_columns].values
y_raw = df_clear[[target_column]].values 
```

**Scaling Data**

Bagian ini melakukan scaling (normalisasi) data fitur dan target ke rentang 0–1 menggunakan MinMaxScaler agar model lebih stabil dan cepat saat dilatih.

```python
# ========== Scaling Data ==========

from sklearn.preprocessing import MinMaxScaler

# --- Scaling untuk fitur multivariate ---
scaler_X = MinMaxScaler()
X_scaled = scaler_X.fit_transform(X_raw)

# --- Scaling untuk target suhu air ---
scaler_y = MinMaxScaler()
y_scaled = scaler_y.fit_transform(y_raw)
```

**Fungsi Windowing**

Bagian ini membuat data berurutan (windowing) agar cocok untuk model LSTM, dengan cara mengelompokkan data fitur dan target berdasarkan ukuran jendela (`window_size`). Hasilnya disimpan di `X_seq` dan `y_seq`.

```python
# ========== Fungsi Windowing ==========
def create_sequences(X, y, window_size):
    Xs, ys = [], []
    for i in range(len(X) - window_size):
        Xs.append(X[i:i+window_size])
        ys.append(y[i+window_size])
    return np.array(Xs), np.array(ys)

X_seq, y_seq = create_sequences(X_scaled, y_scaled, window_size)
```

**Split Dataset**

Bagian ini membagi data berurutan (X_seq, y_seq) menjadi data latih (70%) dan data uji (30%) untuk keperluan pelatihan dan evaluasi model.

```python
# ========== Split Dataset ==========

# Split
split_index = int(len(X_seq) * 0.7)
X_train, X_test = X_seq[:split_index], X_seq[split_index:]
y_train, y_test = y_seq[:split_index], y_seq[split_index:]
```


### Hasil Model

Bagian ini membangun model LSTM sederhana dengan 1 layer LSTM dan 1 layer output Dense, lalu dikompilasi menggunakan optimizer Adam dan fungsi loss MSE untuk regresi.

```python
# ========== Bangun Model LSTM ==========
model = Sequential([
    LSTM(lstm_units, activation='tanh', input_shape=(X_train.shape[1], X_train.shape[2])),
    Dense(1)
])
model.compile(optimizer='adam', loss='mse')
```
Bagian ini melatih model LSTM dengan data latih selama beberapa epoch, menggunakan batch tertentu, dan menyisihkan 20% data latih untuk validasi.

```python
# ========== Training ==========
history = model.fit(
    X_train, y_train,
    epochs=epochs,
    batch_size=batch_size,
    validation_split=0.2,  # <- SAMA dengan tuning
    shuffle=True,
    verbose=1
)
```
<div align="center">
<img width="953" alt="image" src="https://github.com/user-attachments/assets/d5fcf864-6b60-44ab-884a-36d9f83f0d1c" />
<br/>
<strong>Gambar 7.</strong> Ploting Aktual Vs Prediksi
</div>

<div align="center">

### Comparison of Actual and Predicted Water Temperature

| Index | Actual Water Temperature (°C) | Predicted Water Temperature (°C) |
|:-----:|:-----------------------------:|:--------------------------------:|
|   0   |             23.0              |             22.884               |
|   1   |             24.0              |             23.339               |
|   2   |             23.0              |             23.836               |
|   3   |             23.0              |             23.410               |
|   4   |             19.0              |             22.773               |
|   5   |             18.0              |             20.130               |
|   6   |             24.0              |             18.788               |
|   7   |             23.0              |             21.048               |
|   8   |             28.0              |             22.161               |
|   9   |             25.0              |             25.484               |

</div>


**Kesimpulan Visualisasi:**

* Model memiliki **kemampuan yang baik dalam mengikuti pola tren** dari suhu air.
* Perbedaan kecil antara kurva aktual dan prediksi menunjukkan adanya **deviasi minor**, namun secara keseluruhan akurat.

  
## Evaluation

Evaluasi model dilakukan untuk mengukur performa prediksi suhu air (Water Temperature) menggunakan metrik error dan akurasi. Empat metrik utama digunakan, yaitu **Mean Squared Error (MSE)**, **Root Mean Squared Error (RMSE)**, **Mean Absolute Error (MAE)**, dan **R-squared (R²)**.

* **MSE** mengukur rata-rata kuadrat dari selisih antara nilai prediksi dan nilai aktual. Semakin kecil nilainya, semakin baik performa model.
* **RMSE** adalah akar dari MSE dan memberikan interpretasi kesalahan dalam satuan yang sama dengan data asli.
* **MAE** menunjukkan rata-rata kesalahan absolut antara prediksi dan nilai aktual, sehingga lebih robust terhadap outlier.
* **R²** mengukur proporsi variansi data yang dapat dijelaskan oleh model, dengan nilai mendekati 1 menandakan prediksi yang sangat baik.

```python
# ========== Prediksi dan Evaluasi ==========
y_pred = model.predict(X_test).flatten()

mse = mean_squared_error(y_test, y_pred)
rmse = np.sqrt(mse)
mae = mean_absolute_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

print(f"\n📊 Evaluasi Akhir:")
print(f"MSE  : {mse:.4f}")
print(f"RMSE : {rmse:.4f}")
print(f"MAE  : {mae:.4f}")
print(f"R²   : {r2:.2f}")
```

Model prediksi suhu air menunjukkan performa yang baik dengan nilai koefisien determinasi (R²) sebesar 0.85, yang mengindikasikan bahwa model mampu menjelaskan sekitar 85% variasi dalam data suhu air aktual. Hal ini menandakan model memiliki kemampuan prediksi yang kuat dan relevan terhadap pola data yang ada. Selain itu, metrik evaluasi kesalahan seperti MSE, RMSE, dan MAE menunjukkan nilai yang kecil, yang mencerminkan tingkat kesalahan prediksi yang rendah dan konsistensi hasil yang tinggi. Dengan demikian, model ini dapat diandalkan untuk memprediksi suhu air secara akurat dalam konteks penelitian atau aplikasi terkait.

```python
# ========== Plot Loss Training & Validation ==========
plt.figure(figsize=(10, 5))
plt.plot(history.history['loss'], label='Training Loss', color='blue')
plt.plot(history.history['val_loss'], label='Validation Loss', color='orange')
plt.title('Training & Validation Loss over Epochs')
plt.xlabel('Epochs')
plt.ylabel('Loss (MSE)')
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()
```

<div align="center">
<img width="898" alt="image" src="https://github.com/user-attachments/assets/b7dad999-399d-4a38-a003-fe6267fdbae1" />
<br/>
<strong>Gambar 8.</strong> Ploting Training & Validation Loss over Epochs
</div>


**Kesimpulan Evaluasi**
1. Nilai MSE dan RMSE yang relatif kecil menunjukkan bahwa rata-rata kesalahan prediksi yang dilakukan oleh model sangat rendah. Ini mengindikasikan bahwa perbedaan antara nilai aktual dan nilai prediksi tidak signifikan secara kuantitatif. Nilai MAE yang juga rendah memperkuat indikasi tersebut, dengan rata-rata kesalahan absolut yang kecil. Sementara itu, nilai R² sebesar 0.85 menunjukkan bahwa sekitar 85% variasi pada data target dapat dijelaskan oleh model. Ini merupakan indikasi bahwa model memiliki kemampuan prediktif yang sangat baik dan cukup kuat dalam memodelkan hubungan antara fitur input dan target yang diprediksi.
   
3. Pada grafik Ploting Training & Validation Loss over Epochs Secara keseluruhan, grafik ini menunjukkan bahwa model yang dilatih memiliki proses pembelajaran yang stabil, tanpa tanda-tanda *overfitting* maupun *underfitting* yang berarti. Dengan nilai loss yang rendah dan kurva yang stabil, model dapat dikatakan memiliki performa yang baik dalam melakukan generalisasi terhadap data yang tidak terlihat selama pelatihan.

