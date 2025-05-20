# Laporan Proyek Machine Learning - Nama Anda

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
```
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

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

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

