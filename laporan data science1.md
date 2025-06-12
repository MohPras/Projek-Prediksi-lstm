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

#### Setup Environment:

**A. Clone Repository**

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

###### Catatan:

* Pastikan Anda sudah menginstal **Python 3.8 atau lebih tinggi**.
* Gunakan `python` atau `python3` sesuai dengan OS dan pengaturan sistem Anda.
* Jika menggunakan **Anaconda**, Anda bisa membuat environment dengan:

  ```bash
  conda create --name attrition-env python=3.9
  conda activate attrition-env
  pip install -r requirements.txt
  ```

**B. Akses Dataset**

###### Install dan import library
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

###### Dapatkan data
```python
# baca data
url = "https://raw.githubusercontent.com/dicodingacademy/dicoding_dataset/refs/heads/main/employee/employee_data.csv"
df = pd.read_csv(url)
df.head()
```

**C. Akses Dashboard**

- email “mohammadprastya2023@gmail.com” dan password “123Nurdin”

###### Tutorial Singkat: Membuka Dashboard Metabase dari File Backup

**Prasyarat:**
Pengguna telah memiliki Java (JRE 8 atau lebih baru) terinstal dan telah mengunduh file `metabase.jar`.

**Langkah-langkah:**

1.  **Hentikan Layanan Metabase (Jika Sedang Berjalan):**
    * Apabila *instance* Metabase saat ini sedang aktif, harap hentikan prosesnya. Jika dijalankan melalui Command Prompt/Terminal, dapat dihentikan dengan menekan `Ctrl + C`.

2.  **Identifikasi Lokasi Folder Database Metabase:**
    * Temukan folder `.metabase` yang biasanya terletak di direktori *home* pengguna:
        * Untuk Windows: `C:\Users\NamaPengguna\.metabase`
        * Untuk macOS/Linux: `/home/NamaPengguna/.metabase`
    * (Apabila folder ini belum terbentuk, Anda dapat menjalankan `java -jar metabase.jar` satu kali, lalu hentikan prosesnya, dan folder tersebut akan secara otomatis dibuat.)

3.  **Ganti File Database:**
    * **Penting:** Harap **memindahkan atau mengganti nama** file `metabase.db.mv.db` dan `metabase.db.trace.db` yang ada di dalam folder `.metabase` tersebut (sebagai langkah pencadangan).
    * **Salin** kedua file *backup* Anda (`metabase.db.mv.db` dan `metabase.db.trace.db`) ke dalam folder `.metabase` yang telah diidentifikasi. Pastikan nama file tetap sama persis.

4.  **Jalankan Metabase:**
    * Buka Command Prompt atau Terminal.
    * Navigasikan ke direktori tempat file `metabase.jar` berada (contoh: `cd C:\Metabase`).
    * Eksekusi Metabase menggunakan perintah berikut: `java -jar metabase.jar`

5.  **Akses Dashboard:**
    * Setelah Metabase selesai memuat sepenuhnya, buka peramban web (browser) dan kunjungi alamat: `http://localhost:3000`
    * Dashboard Metabase Anda seharusnya kini dapat diakses dan menampilkan data dari file *backup* yang telah disalin.

----------------------------------

## Business Dashboard

Dashboard Monitoring Employee Jaya Maju adalah bussines dashboard yang didesain sefektif mungkin untuk memberikan insight kepada para manajer departemen HR terkait attrition rate yang cukup tinggi hingga lebih dari 10%. Berikut dibawah ini adalah cuplikan dari sebagian dahboard bussines ini untuk melihat fullnya bisa kunjungi link yaitube ini ( https://www.youtube.com/watch?v=JNU13Fjy1sQ ).

<div align="center">
<img src="https://github.com/user-attachments/assets/dafd5df1-c06d-4529-b4f8-bcab5403974b" alt="Gambar 1: Alur Proyek Sistem Rekomendasi" width="800"/>
</div>

### Detail Halamana Pertama

Halaman pertama dashboard ini memberikan tinjauan komprehensif tentang **profil karyawan aktif** dan **tren retensi**. Dengan memvisualisasikan data ini, manajemen dapat dengan mudah mengidentifikasi area kekuatan dan potensi masalah terkait sumber daya manusia, seperti distribusi tenaga kerja yang tidak seimbang atau tingkat *resign* yang tinggi. Berikut adalah penjelasan lebih lanjut mengenai setiap metrik yang disajikan pada halaman pertama dashboard Anda:

* **Jumlah Pekerja Aktif:**
    Metrik ini menunjukkan **total jumlah karyawan yang saat ini aktif** bekerja di perusahaan. Angka ini adalah indikator dasar dari ukuran tenaga kerja Anda dan dapat digunakan untuk melacak pertumbuhan atau penyusutan karyawan dari waktu ke waktu.

* **Distribusi Jumlah Karyawan per Departemen:**
    Bagian ini menyajikan **visualisasi pembagian karyawan di setiap departemen**. Anda dapat dengan cepat melihat departemen mana yang memiliki karyawan terbanyak atau paling sedikit. Informasi ini krusial untuk perencanaan sumber daya, alokasi anggaran, dan identifikasi potensi kelebihan atau kekurangan staf di area tertentu.

* **Jumlah Karyawan *Resign* dan *Stay*:**
    Metrik ini membandingkan **jumlah karyawan yang keluar (*resign*) dengan karyawan yang masih bertahan (*stay*)** dalam periode tertentu. Ini adalah indikator penting untuk kesehatan organisasi dan tingkat retensi karyawan. Tingkat *resign* yang tinggi mungkin menunjukkan masalah dengan kepuasan karyawan, budaya perusahaan, atau kompensasi.

* **Distribusi Jumlah Karyawan Berdasarkan *Gender*:**
    Diagram ini menampilkan **proporsi karyawan berdasarkan jenis kelamin**. Data ini penting untuk memastikan keberagaman dan kesetaraan gender di tempat kerja, serta untuk mematuhi regulasi terkait keberagaman.

* **Total Karyawan Berdasarkan Pendidikan:**
    Metrik ini mengelompokkan **jumlah karyawan berdasarkan tingkat pendidikan terakhir mereka**. Informasi ini berguna untuk memahami kualifikasi umum tenaga kerja Anda dan mengidentifikasi kesenjangan keterampilan yang mungkin memerlukan program pelatihan atau rekrutmen khusus.

* **Total Pekerja Berdasarkan Usia:**
    Bagian ini menunjukkan **distribusi karyawan berdasarkan kelompok usia**. Data ini penting untuk perencanaan suksesi, memahami dinamika tim antar-generasi, dan merancang tunjangan atau program kesehatan yang sesuai dengan demografi usia karyawan.

* **Jumlah Karyawan Berdasarkan Lama Bekerja di Perusahaan (*Tenure*):**
    Metrik ini mengkategorikan **karyawan berdasarkan durasi mereka bekerja di perusahaan** (misalnya, <1 tahun, 1-3 tahun, 3-5 tahun, >5 tahun). Informasi ini membantu mengidentifikasi tren *turnover* pada periode tertentu dan memahami seberapa lama karyawan cenderung bertahan di perusahaan. Angka *tenure* yang rendah, terutama di awal, bisa menjadi sinyal adanya masalah dalam proses *onboarding* atau kepuasan kerja awal.

<div align="center">
<img width="800" alt="image" src="https://github.com/user-attachments/assets/98e3cb70-3c0a-440e-ae43-26d96fbe3f1f" />
</div>

### Detail Halamana Kedua

Halaman kedua dashboard ini didedikasikan untuk **analisis mendalam mengenai tingkat *attrition* (pergantian karyawan)**. Tujuan utama dari halaman ini adalah untuk mengidentifikasi faktor-faktor pendorong di balik keputusan karyawan untuk *resign*, sehingga perusahaan dapat mengembangkan strategi retensi yang lebih efektif dan proaktif. Dengan memahami "mengapa" karyawan pergi, kita bisa mengambil langkah-langkah untuk mengurangi *turnover* yang tidak diinginkan dan mempertahankan talenta terbaik. Berikut adalah penjelasan setiap metrik penting yang disajikan pada halaman kedua dashboard Anda:

* **Pekerja Aktif vs Keluar:**
    Grafik ini memberikan perbandingan langsung antara **jumlah karyawan yang saat ini aktif** dengan **jumlah karyawan yang telah keluar** dalam periode waktu tertentu. Ini adalah titik awal untuk memahami skala *attrition* secara keseluruhan di perusahaan Anda.

* ***Gender* vs *Attrition*:**
    Analisis ini menampilkan **tingkat *attrition* yang terbagi berdasarkan jenis kelamin karyawan**. Dengan metrik ini, kita bisa melihat apakah ada disparitas signifikan dalam tingkat *resign* antara karyawan pria dan wanita. Perbedaan yang mencolok mungkin mengindikasikan isu-isu terkait kesetaraan atau lingkungan kerja yang mempengaruhi satu *gender* lebih dari yang lain.

* ***Age* vs *Attrition*:**
    Visualisasi ini mengamati **bagaimana tingkat *attrition* bervariasi di berbagai kelompok usia karyawan**. Penting untuk mengidentifikasi apakah karyawan muda, paruh baya, atau senior lebih rentan untuk *resign*. Misalnya, *attrition* tinggi di kelompok usia muda mungkin menunjukkan masalah dengan peluang pengembangan karir atau budaya perusahaan, sementara *attrition* di usia senior mungkin berkaitan dengan masalah pensiun atau transisi karir.

* ***Marital Status* vs *Attrition*:**
    Metrik ini menganalisis **hubungan antara status perkawinan karyawan (misalnya, lajang, menikah, cerai) dengan tingkat *attrition***. Terkadang, perubahan status perkawinan dapat memengaruhi prioritas atau kebutuhan karyawan, yang pada gilirannya bisa memengaruhi keputusan mereka untuk bertahan di perusahaan.

* ***OverTime* vs *Attrition*:**
    Bagian ini mengeksplorasi **dampak dari jam kerja lembur (*overtime*) terhadap tingkat *attrition***. Karyawan yang sering atau selalu lembur mungkin mengalami *burnout* atau ketidakseimbangan kehidupan-kerja, yang dapat mendorong mereka untuk mencari peluang lain. Metrik ini membantu mengidentifikasi apakah jam kerja berlebihan menjadi pemicu *resign*.

* ***YearsAtCompany* vs *Attrition*:**
    Analisis ini menunjukkan **hubungan antara lamanya karyawan bekerja di perusahaan (*tenure*) dengan kemungkinan mereka untuk *resign***. Dengan metrik ini, kita dapat melihat pada titik *tenure* mana karyawan cenderung paling sering keluar. Misalnya, tingkat *attrition* yang tinggi pada tahun-tahun awal mungkin menandakan masalah dengan proses *onboarding* atau harapan kerja yang tidak terpenuhi.

* ***TotalWorkingYears* vs *Attrition*:**
    Berbeda dengan *YearsAtCompany*, metrik ini melihat **pengaruh total pengalaman kerja karyawan (tidak hanya di perusahaan saat ini) terhadap *attrition***. Ini bisa membantu memahami apakah karyawan dengan pengalaman kerja yang sangat sedikit atau sangat banyak memiliki kecenderungan *attrition* yang berbeda, yang mungkin terkait dengan tujuan karir atau ekspektasi mereka.

* ***WorkLifeBalance* vs *Attrition*:**
    Metrik ini menyajikan **korelasi antara persepsi karyawan tentang keseimbangan kehidupan-kerja mereka dengan tingkat *attrition***. Keseimbangan yang buruk adalah pemicu *resign* yang umum. Data ini dapat menyoroti pentingnya kebijakan dan program yang mendukung *work-life balance*.

* ***JobSatisfaction* vs *Attrition*:**
    Analisis ini menunjukkan **hubungan antara tingkat kepuasan kerja karyawan dengan keputusan mereka untuk *resign***. Secara intuitif, karyawan yang tidak puas dengan pekerjaan mereka cenderung lebih mungkin untuk pergi. Metrik ini dapat membantu mengidentifikasi departemen atau peran di mana kepuasan kerja rendah dan menjadi faktor *attrition*.

* ***DistanceFromHome* vs *Attrition*:**
    Bagian ini mengkaji **bagaimana jarak antara rumah karyawan dan kantor memengaruhi tingkat *attrition***. Jarak tempuh yang sangat jauh atau biaya transportasi yang tinggi bisa menjadi beban bagi karyawan, terutama jika ada pilihan pekerjaan yang lebih dekat.

* ***JobRole* vs *Attrition*:**
    Metrik ini menampilkan **tingkat *attrition* yang dibagi berdasarkan peran pekerjaan (Job Role) karyawan**. Ini adalah metrik yang sangat penting untuk mengidentifikasi peran-peran spesifik yang memiliki tingkat *turnover* tinggi. Dengan demikian, tim HR dapat menyelidiki lebih lanjut masalah yang mungkin ada pada peran-peran tersebut, seperti beban kerja, kompensasi, atau jalur karir yang tidak jelas.

----------------------------------

## Conclusion

### Kesimpulan Demografi Karyawan

Dashboard ini menampilkan **879 pekerja aktif** dengan profil demografi yang khas. Mayoritas adalah **laki-laki (58.6%)** dan **sudah menikah (43.86%)**. Dalam hal kualifikasi, sebagian besar karyawan berpendidikan **sarjana (38.75%)**. Pekerja didominasi oleh kelompok **usia 25-34 tahun (37.90%)**, menunjukkan tenaga kerja yang relatif muda. Menariknya, sejumlah besar karyawan, yaitu **325 orang**, telah bekerja di perusahaan selama **6 hingga 10 tahun**, mengindikasikan retensi yang kuat pada segmen karyawan menengah.

### Kesimpulan Analisis *Attrition Rate*

Analisis tingkat *attrition* mengungkap beberapa tren penting yang dapat menjadi dasar strategi retensi. Secara keseluruhan, perusahaan menunjukkan **tingkat retensi karyawan yang relatif baik**, dengan **83% pekerja memilih untuk bertahan**. Meskipun demikian, ada beberapa area yang perlu diperhatikan:

* **Pekerja Muda dan Lajang Paling Rentan:** Karyawan di **usia muda (18-25 tahun)** menunjukkan persentase *attrition* tertinggi **(sekitar 38%)**. Tren serupa terlihat pada pekerja **lajang**, yang memiliki persentase *attrition* paling tinggi **(26.7%)**.
* **Dampak Buruk dari Lembur dan Keseimbangan Hidup-Kerja:** **Lembur** secara signifikan meningkatkan *attrition* menjadi **31.92%**, jauh lebih tinggi dari mereka yang tidak lembur. Sejalan dengan itu, **keseimbangan hidup-kerja yang "Sangat Buruk"** juga menjadi pemicu *resign*.
* **Karyawan Baru dan Berpendapatan Rendah Rentan Keluar:** Tingkat *turnover* sangat tinggi pada **karyawan baru (0-2 tahun masa kerja)** dengan *attrition* mencapai **29.96%**. Selain itu, karyawan dengan **pendapatan bulanan kurang dari 3 juta** memiliki persentase *attrition* yang sangat tinggi **(71.33%)**, menunjukkan sensitivitas terhadap kompensasi.
* **Kepuasan Kerja dan Jarak Tempuh Berperan:** Karyawan dengan **kepuasan kerja "Sangat Tidak Puas"** memiliki tingkat *attrition* yang lebih dari dua kali lipat dibandingkan mereka yang "Sangat Puas." Jarak rumah dari kantor juga menjadi faktor; semakin jauh, semakin tinggi *attrition*, terutama bagi yang tinggal **21+ km dari kantor**.
* **Peran "Sales Representative" Memiliki Tantangan Retensi:** Posisi **"Sales Representative"** menonjol dengan persentase *attrition* tertinggi **(43.1%)**, mengindikasikan adanya masalah spesifik pada peran ini yang perlu diinvestigasi.
* **Secara umum, karyawan yang lebih senior (usia 46-55 tahun) dan yang sudah menikah cenderung lebih stabil**.


### Rekomendasi Action Items (Optional)

---

## Rekomendasi *Action Items* untuk HR

Berdasarkan kesimpulan demografi karyawan dan analisis tingkat *attrition*, berikut adalah rekomendasi *action items* strategis untuk tim HR:

### Dari Demografi Karyawan:

1.  **Fokus pada Pengembangan Karyawan Muda dan Menengah:**
    * **Tindakan:** Karena mayoritas karyawan berada di kelompok usia 25-34 tahun dan banyak yang memiliki masa kerja 6-10 tahun, **prioritaskan program pengembangan karier dan kepemimpinan** yang dirancang untuk kelompok ini. Ini akan membantu mereka melihat jalur kemajuan yang jelas di perusahaan dan meningkatkan loyalitas jangka panjang.
    * **Manfaat:** Memastikan talenta muda dan menengah terus berkembang dan merasa dihargai, mengurangi risiko stagnasi karier.

2.  **Kaji Kebijakan Keberagaman Gender dan Status Perkawinan:**
    * **Tindakan:** Meskipun mayoritas karyawan adalah laki-laki dan sudah menikah, penting untuk **memastikan kebijakan dan benefit perusahaan mendukung semua *gender* dan status perkawinan**. Lakukan survei *engagement* atau *focus group discussion* untuk memahami kebutuhan spesifik, misalnya, dukungan untuk orang tua baru atau *benefit* yang relevan bagi lajang.
    * **Manfaat:** Menciptakan lingkungan kerja yang inklusif dan adil untuk semua karyawan, mendukung keberagaman di tempat kerja.

### Dari Analisis *Attrition Rate*:

1.  **Perbaiki Strategi Retensi untuk Karyawan Baru dan Berpendapatan Rendah:**
    * **Tindakan:** Tingkat *attrition* yang sangat tinggi pada karyawan baru (0-2 tahun) dan mereka dengan pendapatan di bawah 3 juta sangat mengkhawatirkan. **Reviu proses *onboarding* dan *mentoring* untuk karyawan baru** agar mereka merasa lebih terhubung dan didukung. Selain itu, **evaluasi struktur gaji, terutama untuk posisi *entry-level* atau berpendapatan rendah**, untuk memastikan daya saing dan kelayakan hidup.
    * **Manfaat:** Mengurangi *turnover* di awal masa kerja, meningkatkan investasi pada talenta baru, dan memastikan kompensasi yang adil dan kompetitif.

2.  **Mitigasi Dampak Lembur dan Promosikan Keseimbangan Hidup-Kerja:**
    * **Tindakan:** Tingkat *attrition* yang tinggi akibat lembur dan keseimbangan hidup-kerja yang buruk menuntut perhatian serius. **Identifikasi departemen atau tim dengan tingkat lembur yang tinggi** dan selidiki akar permasalahannya (misalnya, beban kerja tidak realistis, kekurangan staf). **Terapkan kebijakan yang lebih ketat terkait jam kerja lembur** dan **promosikan inisiatif keseimbangan hidup-kerja** (misalnya, jam kerja fleksibel, hari kesehatan mental, program *wellness*).
    * **Manfaat:** Meningkatkan kesehatan mental dan fisik karyawan, mengurangi *burnout*, dan meningkatkan kepuasan kerja secara keseluruhan.

3.  **Prioritaskan Dukungan untuk Karyawan Muda dan Lajang:**
    * **Tindakan:** Kelompok usia 18-25 tahun dan karyawan lajang menunjukkan tingkat *attrition* yang signifikan. **Kembangkan program retensi yang ditargetkan** untuk mereka, seperti peluang pengembangan karier yang jelas, program *networking*, atau inisiatif sosial yang mendukung kebutuhan mereka.
    * **Manfaat:** Mempertahankan talenta muda yang prospektif dan memastikan karyawan lajang juga merasa memiliki koneksi dan dukungan di tempat kerja.

4.  **Investigasi dan Tingkatkan Kepuasan Kerja serta Lingkungan Kerja:**
    * **Tindakan:** Tingkat kepuasan kerja yang rendah dan jarak rumah yang jauh berkorelasi dengan *attrition*. **Lakukan survei kepuasan kerja secara berkala** dan tindak lanjuti hasilnya dengan serius. Pertimbangkan **opsi kerja hibrida atau fleksibel** untuk mengurangi beban komuter bagi karyawan yang tinggal jauh.
    * **Manfaat:** Menciptakan lingkungan kerja yang lebih positif, nyaman, dan mendukung, yang pada akhirnya meningkatkan retensi.

5.  **Perhatian Khusus pada Peran "Sales Representative":**
    * **Tindakan:** Persentase *attrition* yang sangat tinggi pada *Sales Representative* membutuhkan penyelidikan mendalam. **Lakukan *exit interview* yang komprehensif** untuk memahami alasan kepergian mereka. **Evaluasi kembali beban kerja, target, kompensasi, dan dukungan yang diberikan** kepada peran ini. Pertimbangkan program pelatihan atau *coaching* khusus untuk mengatasi tantangan yang mereka hadapi.
    * **Manfaat:** Mengurangi *turnover* di posisi kunci, menjaga stabilitas tim penjualan, dan melindungi pendapatan perusahaan.

Rekomendasi ini akan menjadi titik awal yang kuat bagi tim HR untuk menyusun strategi yang lebih terarah dalam mengelola dan mempertahankan talenta terbaik perusahaan.
