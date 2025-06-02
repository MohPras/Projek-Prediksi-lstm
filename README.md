# Proyek Akhir: Menyelesaikan Permasalahan attrition rate di perusahaan multinasional Jaya Jaya Maju

## Business Understanding

<div align="center">
<img src="https://github.com/user-attachments/assets/c901980e-c86b-42a7-9979-3f6a8dfee4a6" alt="Gambar 1: Alur Proyek Sistem Rekomendasi" width="800"/>
</div>

### Latar Belakang 

#### Latar Belakang Bisnis Jaya Jaya Maju

Jaya Jaya Maju adalah sebuah perusahaan multinasional yang telah berdiri sejak tahun 2000 dan berkembang pesat hingga memiliki lebih dari 1000 karyawan yang tersebar di berbagai wilayah di negeri ini. Sebagai perusahaan besar yang terus berusaha untuk meningkatkan kinerja dan ekspansinya, manajemen Jaya Jaya Maju sangat bergantung pada sumber daya manusia yang berkualitas dan produktif.

Namun, meskipun sudah memiliki skala yang besar, perusahaan menghadapi tantangan serius dalam pengelolaan karyawan, terutama terkait tingginya tingkat attrition rate, yaitu rasio karyawan yang keluar dari perusahaan dibandingkan dengan total karyawan secara keseluruhan. Saat ini, attrition rate perusahaan sudah melebihi 10%, yang dapat berdampak negatif terhadap stabilitas operasional, produktivitas, dan biaya yang dikeluarkan untuk rekrutmen dan pelatihan karyawan baru.

Masalah ini menjadi perhatian utama departemen Human Resources (HR), yang ingin memahami faktor-faktor utama penyebab tingginya attrition tersebut dan berupaya melakukan langkah-langkah strategis untuk mengurangi angka tersebut. Untuk itu, diperlukan analisis mendalam dan sistem pemantauan yang efektif agar manajemen dapat mengambil keputusan berbasis data dan melakukan intervensi tepat waktu dalam pengelolaan karyawan.

------------------------------

### Permasalahan Bisnis

#### Permasalahan Bisnis yang Akan Diselesaikan

1. **Tingginya Tingkat Attrition Karyawan**
   Jaya Jaya Maju mengalami tingkat attrition yang cukup tinggi, lebih dari 10%, yang menyebabkan kehilangan karyawan secara signifikan dan berdampak pada stabilitas operasional perusahaan.

2. **Kesulitan dalam Mengidentifikasi Faktor Penyebab Attrition**
   Perusahaan belum memiliki pemahaman yang jelas dan terstruktur mengenai faktor-faktor apa saja yang menyebabkan karyawan memilih untuk keluar dari perusahaan.

3. **Kurangnya Sistem Monitoring yang Efektif untuk HR**
   Departemen HR belum memiliki dashboard atau alat pemantauan yang mudah diakses dan informatif untuk memonitor kondisi karyawan dan faktor-faktor risiko yang berkontribusi pada attrition secara real-time.

4. **Tantangan dalam Pengambilan Keputusan Berbasis Data**
   Kurangnya insight dan data analitik membuat manajemen kesulitan dalam mengambil tindakan preventif yang tepat dan terukur untuk mengurangi tingkat attrition.

5. **Dampak Negatif dari Attrition terhadap Biaya dan Produktivitas**
   Tingginya attrition meningkatkan biaya rekrutmen, pelatihan, serta mengurangi produktivitas akibat kehilangan karyawan berpengalaman dan perlu adaptasi karyawan baru.

------------------------------

### Cakupan Proyek

#### Cakupan Proyek

1. **Pengumpulan dan Pemahaman Data**

   * Mengumpulkan dataset karyawan yang mencakup informasi demografi, pekerjaan, performa, dan status keluar masuk karyawan.
   * Memahami struktur dan kualitas data yang tersedia.

2. **Eksplorasi Data dan Analisis Deskriptif**

   * Melakukan eksplorasi data untuk mengetahui pola distribusi karyawan dan tren attrition.
   * Mengidentifikasi hubungan awal antara berbagai faktor dengan tingkat attrition.

3. **Identifikasi Faktor Penyebab Attrition**

   * Menggunakan teknik statistik dan machine learning untuk mengidentifikasi variabel yang berpengaruh signifikan terhadap keputusan karyawan untuk keluar.
   * Membuat model prediktif untuk menentukan risiko attrition karyawan.

4. **Pengembangan Dashboard Bisnis**

   * Merancang dan membangun dashboard interaktif menggunakan Metabase yang menampilkan metrik-metrik penting terkait attrition dan faktor-faktor pendukungnya.
   * Memastikan dashboard dapat diakses dan dipahami oleh manajer HR untuk monitoring dan pengambilan keputusan.

5. **Rekomendasi Strategi dan Tindak Lanjut**

   * Memberikan insight dan rekomendasi berbasis data kepada manajemen HR untuk mengurangi tingkat attrition.
   * Menyusun langkah-langkah strategis yang bisa diambil berdasarkan hasil analisis.

6. **Membuat Model Machine Learning**

   * Mengembangkan model machine learning berbasis klasifikasi untuk memprediksi status karyawan berdasarkan variabel-variabel faktor penyebab attrition

------------------------------

### Persiapan

**Data source:** [Employee data](https://github.com/dicodingacademy/dicoding_dataset/tree/main/employee 'Dicoding GitHub - Employee data')

#### Setup environment:

Ikuti langkah-langkah berikut untuk menjalankan proyek ini di lingkungan lokal Anda:

1. **Clone Repository**

   ```bash
   git clone <URL-repo>
   ```

2. **Buat dan Aktifkan Virtual Environment**

   * **Untuk Windows:**

     ```bash
     python -m venv venv
     venv\Scripts\activate
     ```

   * **Untuk macOS/Linux:**

     ```bash
     python3 -m venv venv
     source venv/bin/activate
     ```

3. **Install Dependencies**

   ```bash
   pip install -r requirements.txt
   ```

##### Catatan:

* Pastikan Anda sudah menginstal **Python 3.8 atau lebih tinggi**.
* Gunakan `python` atau `python3` sesuai dengan OS dan pengaturan sistem Anda.
* Jika menggunakan **Anaconda**, Anda bisa membuat environment dengan:

  ```bash
  conda create --name attrition-env python=3.9
  conda activate attrition-env
  pip install -r requirements.txt
  ```

#### Install dan import library
```python
# install library
!pip install xgboost

# ---- # import library ----
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
# ---- preprocesing data ----
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import LabelEncoder, StandardScaler, MinMaxScaler
from sklearn.model_selection import train_test_split
from imblearn.under_sampling import RandomUnderSampler
from collections import Counter
# ---- klasifikasi xgb ----
from xgboost import XGBClassifier
from sklearn.model_selection import GridSearchCV
# ---- random forest klasifikasi ----
from sklearn.ensemble import RandomForestClassifier
# ---- save model ----
import joblib
# ---- evaluasi ----
from sklearn.metrics import accuracy_score, f1_score, classification_report, precision_score, recall_score, confusion_matrix, ConfusionMatrixDisplay, roc_auc_score
from sklearn.metrics import ConfusionMatrixDisplay

# ---- Set style ----
sns.set(style='whitegrid')
```

#### Dapatkan data
```python
# baca data
url = "https://raw.githubusercontent.com/dicodingacademy/dicoding_dataset/refs/heads/main/employee/employee_data.csv"
df = pd.read_csv(url)
df.head()
```

## Business Dashboard

Jaya Jaya Maju Employees Dashboard adalah bussines dashboard yang didesain sefektif mungkin untuk memberikan insight kepada para manajer departemen HR terkait attrition rate yang cukup tinggi hingga lebih dari 10%.

## Conclusion

Jelaskan konklusi dari proyek yang dikerjakan.

### Rekomendasi Action Items (Optional)

Berikan beberapa rekomendasi action items yang harus dilakukan perusahaan guna menyelesaikan permasalahan atau mencapai target mereka.

- action item 1
- action item 2
