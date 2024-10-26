# 1. EDA and Insights from Dataset
## Descriptive Statistics
- Dataset dailyactivity_merged memiliki 940 baris dan 15 kolom. Semua kolom memiliki tipe data yang sesuai dengan isinya. Nama kolom juga sudah mencerminkan informasi yang terkandung di dalamnya dengan baik.
- Tidak ada kolom yang memiliki nilai kosong (null values), dan tidak ditemukan baris duplikat dalam dataset.
- Berdasarkan analisis summary statistik dari kolom-kolom yang ada, tidak ada nilai yang tampak janggal atau tidak wajar pada kolom-kolom tersebut. Nilai minimum, rata-rata, median, maksimum, serta distribusi lainnya terlihat sesuai dengan data aktivitas pengguna.
### Mengecek Null
![image](https://github.com/user-attachments/assets/1abf3e1d-8c83-49eb-b654-464a02c751a0)

Tidak ada null pada data.
## Univariate Analysis
- KDE Plot
  
  ![image](https://github.com/user-attachments/assets/0e059159-6f20-480b-8420-0564148664cb)
  Diketahui kolom Calories terdistribusi cukup normal, beberapa kolom lainnya  cenderung skew positive dan bimodal.

- Box Plot
  ![Untitled](https://github.com/user-attachments/assets/6e35ca62-a319-42f0-a782-18e9f7d9c57b)
  Pada analisis univariate dengan boxplot, diketahui terdapat outliers pada semua kolom kecuali Sedentary Minutes. Kami menganggap data outlier ini adalah data asli, dengan mempertimbangkan kemungkinan bahwa pengguna outlier tersebut merupakan atlet.

## Multivariate Analysis
- Correlation Heatmap
  ![image](https://github.com/user-attachments/assets/22077249-4ac8-41f2-8133-312fb8f6b893)
  - Beberapa fitur yang berpotensi menjadi redundan karena korelasinya yang terlalu kuat adalah:
    - TotalSteps, TotalDistance, dan TrackerDistance
    - FairlyActiveMinutes dan ModeratelyActiveDistance
    - LightActiveDistance dan LightlyActiveMinutes
  - Beberapa fitur dengan korelasi kuat terhadap target Calories adalah:
    - TrackerDistance: Korelasi positif sebesar 0.65.
    - TotalDistance: Korelasi positif sebesar 0.64.
    - VeryActiveMinutes: Korelasi positif sebesar 0.62.
    - TotalSteps: Korelasi positif sebesar 0.59.
    - Korelasi negatif yang kecil ditemukan pada SedentaryMinutes (-0.11), menunjukkan bahwa semakin lama waktu duduk, semakin sedikit kalori yang dibakar.

## Insight Extraction
![image](https://github.com/user-attachments/assets/7fe1816e-c004-4af3-841c-d19ec610cc9e)

Terdapat 29 pengguna yang tergolong sebagai frequent users (menggunakan Fitbit lebih dari 20 hari), 3 pengguna sebagai casual users (menggunakan Fitbit antara 10 hingga 20 hari), dan 1 pengguna sebagai inactive user (menggunakan Fitbit kurang dari 10 hari).

![image](https://github.com/user-attachments/assets/5890b6f7-2fbe-4378-ad9b-9a946922f634)

Pengelompokan kategori aktivitas
- Sedentary (Tidak Aktif): 0 - 4999 langkah 
- Low Active (Aktif Rendah): 5000 - 7499 langkah
- Somewhat Active (Aktif Sedang): 7500 - 9999 langkah
- Active (Aktif): 10,000 - 12,499 langkah
- Highly Active (Sangat Aktif): 12,500 langkah ke atas

Masih Banyak Pengguna dalam Kategori Sedentary: Data ini menunjukkan bahwa mayoritas pengguna belum memanfaatkan fungsi tracker aktivitas Fitbit secara maksimal untuk meningkatkan aktivitas fisik harian mereka. Banyak pengguna yang lebih banyak menghabiskan waktu dalam aktivitas yang sangat minim (Sedentary). Hal ini mungkin mencerminkan gaya hidup yang kurang aktif atau rendahnya motivasi untuk meningkatkan aktivitas harian mereka.

![image](https://github.com/user-attachments/assets/16562787-82e7-4045-9292-fc8d4f56e442)

Rata-Rata Kalori Terbakar setiap Jamnya

Kalori pengguna terbakar lebih banyak mulai jam 5 pagi dan mulai menurun setelah jam 7 malam. Kemungkinan pengguna lebih aktif dari jam 5 pagi hingga 7 malam setiap hari karena orang biasanya sedang bekerja atau belajar selama rentang waktu tersebut.

![image](https://github.com/user-attachments/assets/1928bae6-b78e-4fcb-a7c9-925fd9995398)

Jarak tempuh memiliki pengaruh signifikan terhadap kalori yang dibakar

Atribut seperti TotalDistance dan Calorie menunjukkan korelasi positif yang kuat dengan Calories. Ini berarti semakin jauh jarak yang ditempuh pengguna, semakin banyak kalori yang dibakar. Visualisasi heatmap dan scatter plot mendukung insight ini.

![image](https://github.com/user-attachments/assets/799db392-2239-47f5-8713-1d9693d8ebe8)

Jarak tempuh memiliki pengaruh signifikan terhadap kalori yang dibakar

Atribut seperti TotalDistance dan ActiveMinutes menunjukkan korelasi positif yang kuat dengan Calories. Ini berarti semakin lama waktu aktif pengguna, semakin banyak kalori yang dibakar. Visualisasi scatter plot mendukung insight ini.

![image](https://github.com/user-attachments/assets/e83444cd-0558-41f8-9c77-f1b57201d91e)

Rata-rata step per hari pada pengguna FitBit cenderung fluktuatif. Rata-rata step tertinggi ada di hari Selasa dan Sabtu, dan rata-rata terendah ada di hari Minggu

![image](https://github.com/user-attachments/assets/42c0df89-6f66-447c-b40c-6c4e62d0bb89)

Pola Aktivitas Mingguan:

Pola Aktivitas Konsisten Senin hingga Jumat: Dari hari Senin hingga Jumat, pola aktivitas terlihat cukup konsisten dengan lonjakan langkah mulai pukul 7:00 hingga 19:00. Hal ini dapat dikaitkan dengan rutinitas harian pengguna selama hari kerja.
Aktivitas Puncak pada Sabtu: Sabtu menunjukkan lonjakan aktivitas yang signifikan antara pukul 11:00 hingga 14:00, dengan warna yang sangat merah tua. Ini mungkin disebabkan oleh meningkatnya kegiatan selama akhir pekan, seperti olahraga, belanja, atau aktivitas sosial.
Penurunan Aktivitas pada Minggu Pagi: Pada Minggu, ada penurunan aktivitas langkah pada pagi hari hingga sekitar pukul 10:00. Aktivitas baru meningkat setelah pukul 10:00, tetapi intensitasnya lebih rendah dibandingkan hari Sabtu, mungkin karena sebagian pengguna menghabiskan pagi hari dengan istirahat atau aktivitas santai.

![image](https://github.com/user-attachments/assets/11e4f4a6-fc40-41ee-9e97-2cf138a7e6d5) ![image](https://github.com/user-attachments/assets/5a0e5423-35ca-48fb-a131-fb8e0299e58b)
- Pada LoggedActivitiesDistance, dapat dilihat bahwa user tidak menginput aktivitas yang mereka lakukan pada Sabtu dan Minggu (weekend), dan hanya ada sedikit aktivitas yang diinput manual pada hari Jum'at.
- Pada SedentaryActiveDistance, rata-rata terendah terdapat pada hari Minggu, pengguna lebih sedikit bergerak secara ringan pada hari tersebut. Artinya, mereka cenderung lebih sering duduk diam atau tidak bergerak sama sekali.

![image](https://github.com/user-attachments/assets/7c0899b2-88f3-4f45-9396-aeff03b0e933)
- Korelasi tinggi (0.93) antara Total Time in Bed dan Total Minutes Asleep, menunjukkan bahwa semakin lama seseorang berada di tempat tidur, semakin lama waktu tidurnya.
- Distribusi waktu tidur dan waktu di tempat tidur menunjukkan bahwa sebagian besar pengguna tidur antara 350 hingga 500 menit (sekitar 6-8 jam), dengan sedikit pengguna yang tidur lebih dari 700 menit.

![image](https://github.com/user-attachments/assets/d079799a-f934-4b06-9c0a-5f7098a6f919)

Variasi Durasi Tidur: Sebagian besar pengguna berada di cluster yang tidur sekitar 400-600 menit (6-10 jam) dengan waktu di tempat tidur yang proporsional. Namun, ada beberapa titik yang menunjukkan variasi yang cukup besar, di mana beberapa orang tidur lebih sedikit meskipun berada di tempat tidur untuk waktu yang lebih lama, yang menunjukkan inefisiensi tidur.

Efisiensi Tidur yang Umum: Sebagian besar data menunjukkan bahwa waktu tidur efektif (Total Minutes Asleep) berada di sekitar 80-90% dari waktu di tempat tidur (Total Time in Bed), dengan sedikit pengguna yang berada di bawah 50%.

![image](https://github.com/user-attachments/assets/51f11df3-3914-4632-89dd-ab44373f99f8)
- Durasi Tidur Lebih Lama dengan Sleep Records yang Lebih Banyak: Pengguna dengan 3 Sleep Records per hari memiliki waktu tidur rata-rata yang lebih tinggi (sekitar 600 menit atau 10 jam) dibandingkan dengan pengguna dengan 1 atau 2 Sleep Records. Hal ini bisa berarti mereka yang tidur lebih dari sekali dalam sehari cenderung mendapatkan lebih banyak total waktu tidur, mungkin karena tidur siang atau tidur terpisah.
- Variasi yang Lebih Besar pada Sleep Records 1: Pada pengguna dengan 1 Sleep Record, terdapat variabilitas yang tinggi, dengan banyak outlier di kedua ujung (waktu tidur sangat singkat dan sangat panjang). Ini menunjukkan beberapa pengguna yang tidur dengan durasi sangat pendek (sekitar 100 menit), sementara beberapa lainnya tidur hingga 800 menit (lebih dari 13 jam).

# 2. Pre-Processing
- Pada dataset 'dailyActivity_merged.csv', mengubah data type pada kolom 'ActivityDate' dari object menjadi date.
- Pada dataset 'minuteMETsNarrow_merged.csv', mengubah data type pada kolom 'ActivityDate' dari object menjadi date.
- Dataset 'minuteMETsNarrow_merged.csv' dikelompokkan 'group', berdasarkan jumlah (Total_METs) dan mean (Avg_METs).
- Menggabungkan (merge) dataset 'dailyActivity_merged.csv' dan 'minuteMETsNarrow_merged.csv'.
- Drop kolom Id

## Data Cleansing

### Handle Duplicated Data
- Terdapat 1 baris data duplikat, data tersebut kemudian di-drop.

### Handle Missing Values
- Pada kolom 'Total_METs' dan 'Avg_METs', masing-masing terdapat 0.64% data null.
- Data null kemudian diisi dengan median.

### Handle Outliers
![image](https://github.com/user-attachments/assets/5fd516fa-eee0-4bc5-ad2f-62daca740b49)
- Berdasarkan boxplot, dapat outliers pada setiap kolom.
- Data FitBit adalah data yang dicapture real-time menggunakan sebuah device. Pada dataset ini, outlier tidak dianggap karena data yang dihasilkan oleh pengguna FitBit sangat beragam, mulai dari orang dengan tingkat aktif rendah hingga tinggi. Oleh karena itu, walaupun distribusi data menunjukkan banyaknya outlier, dapat diasumsikan bahwa itu bukan outlier, namun merupakan data asli.

## Feature Engineering

### Feature Extraction
1. Extract nama hari('DayOfWeek'), tanggal ('Day'), bulan ('Month'), tahun ('Year'), dan is_weekend dan drop 'ActivityDate'.
2. Menambahkan kolom 'DistancePerStep' dengan membagi 'TotalDistance' dan 'TotalStep'
3. Menambahkan kolom 'ActiveRation' dengan menambahkan 'VeryActiveMinutes' + 'FairlyActiveMinutes' + 'LightlyActiveMinutes' dan membaginya dengan 1440 (jumlah menit dalam satu hari).
4. Menambahkan kolom 'ActiveDistanceRatio' dengan menambahkan 'ModeratelyActiveDistance' + 'LightActiveDistance' dan membaginya dengan 'TotalDistance'.
5. Membuat kolom baru yaitu pembagian kelompok berdasarkan total langkah harian
Berdasarkan jurnal Revisiting "How Many Steps Are Enough?" oleh TUDOR-LOCKE, CATRINE1; HATANO, YOSHIRO3; PANGRAZI, ROBERT P.2; KANG, MINSOO4. Diketahui dalam jurnal tersebut, pembagian langkah (steps) seringkali dikategorikan berdasarkan total langkah yang diambil dalam sehari. Berikut adalah pembagian umum yang sering digunakan berdasarkan total langkah:
     - Sedentary (Tidak Aktif): 0 - 4999 langkah, ditandai dengan 0 pada kolom.
     -  Low Active (Aktif Rendah): 5000 - 7499 langkah, ditandai dengan 1 pada kolom.
     -  Somewhat Active (Aktif Sedang): 7500 - 9999 langkah, ditandai dengan 2 pada kolom.
     -  Active (Aktif): 10,000 - 12,499 langkah, ditandai dengan 3 pada kolom.
     -  Highly Active (Sangat Aktif): 12,500 langkah ke atas, ditandai dengan 4 pada kolom.
Pembagian ini membantu dalam memahami tingkat aktivitas fisik individu dan dapat digunakan untuk menetapkan tujuan aktivitas sehari-hari. Maka akan dilakukan penambahan kolom tingkat aktif tidaknya berdasarkan total steps yang telah ditempuh pada hari tersebut.
6. Menambahkan kolom 'TotalUsageMinutes' dengan menjumlahkan 'VeryActiveMinutes'+ 'FairlyActiveMinutes' + 'LightlyActiveMinutes' + 'SedentaryMinutes'.
7. Membuat kolom ratio VeryActiveMinutes, FairlyActiveMinutes, LightlyActiveMinutes, dan SedentaryMinutes dengan membagi masing-masing kolom dengan TotalUsageMinutes.
8. Menghitung jumlah TotalDistance dengan menjumlahkan 'VeryActiveDistance' + 'ModeratelyActiveDistance' + 'LightActiveDistance'.
9. Menambahkan jumlah TotalActiveMinutes dengan menjumlahkan 'VeryActiveMinutes' + 'FairlyActiveMinutes' + 'LightlyActiveMinutes'.
10. Menambahkan kolom 'ActiveRatio' dengan membagi 'TotalActiveMinutes' dengan 1440.
11. Menambahkan kolom 'AverageActiveMinutes'
12. Menambahkan kolom 'AveragePace' dengan membagi 'TotalDistance' dan 'TotalActiveMinutes' kemudian membaginya dengan 60.
13. Menambahkan kolom 'InactiveRatio' dengan membagi 'SedentaryMinutes' dan 1440.

#### Clustering
- Clustering dilakukan menggunakan metode GMM (Gaussian Mixture Model).
- Sebelum clustering, dilakukan scaling terlebih dahulu karena range data agak berbeda jauh, terutama antara steps dan minutes.
- AIC dan BIC yang dihasilkan sama-sama rendah ketika jumlah cluster ada 18, oleh karena itu disimpulkan bahwa jumlah cluster yang optimal adalah 18.
- Clustering kemudian dilakukan menggunakan GMM dengan hard assignment. GMM menghasilkan cluster yang tumpang tindih, sehingga setiap data dapat memiliki lebih dari 1 Cluster. Oleh karena itu, dengan menggunakan hard assignment maka 1 data point hanya akan memiliki 1 cluster.

##### Check Cluster dengan boxplot
![image](https://github.com/user-attachments/assets/39913b3c-9c76-42b1-9870-e55ecc21c376)
![image](https://github.com/user-attachments/assets/478125d6-d4ed-434c-adaa-bc66b37f4aa6)
![image](https://github.com/user-attachments/assets/7ecad1f3-468e-40f7-88e1-49807aa30af5)
![image](https://github.com/user-attachments/assets/43c9b228-792d-4069-80c3-29fd341f6e4f)
![image](https://github.com/user-attachments/assets/27f39f82-8cea-498c-82ab-399dee3e0d5a)
![image](https://github.com/user-attachments/assets/920f31a7-12df-427b-bc80-fe0631fe4716)
![image](https://github.com/user-attachments/assets/a635a57b-7562-436e-aa8b-24505cb907f6)
![image](https://github.com/user-attachments/assets/938389cc-69f9-429c-a0ed-2aec2e2cb77e)
![image](https://github.com/user-attachments/assets/68a5bdfa-40c9-4531-99e3-ef2813e9de69)
![image](https://github.com/user-attachments/assets/e06f694b-662c-4504-a283-0883a99bed22)
![image](https://github.com/user-attachments/assets/b485f4d0-e054-41af-b7f0-a753c1fa0d69)
![image](https://github.com/user-attachments/assets/f8ca1ebb-31c3-424a-9b60-228ae120ebfa)
![image](https://github.com/user-attachments/assets/b039d297-3a5e-4895-a9d4-0c67732a67e2)

- Tidak ditemukan pola distribusi yang jelas pada boxplot. Sehingga akan dicoba caara lain.

##### Check Cluster dengan Heatmap
![image](https://github.com/user-attachments/assets/a2d7a66a-5a60-4268-a653-4f218312aec4)
- Pada heatmap, pola yang terlihat jelas pada 'TotalSteps' dan 'Total_MET'. Oleh karena itu, akan diurutkan berdasarkan hasil ini. Hasilnya akan dimasukkan ke dalam variabel 'ActivityRank'.

##### Mengurutkan Cluster
![image](https://github.com/user-attachments/assets/99274327-652c-4216-8b1e-7b9e77eca592)
- Karena cluster bisa diurutkan, maka kita akan mengambil kolom ActivityRank, dan tidak menggunakan Cluster lagi. Hal ini dilakukan untuk membuat machine learning mampu menangkap pola urutan yang ada pada data ini. Namun, akan dilakukan pengecekan ulang di feature selection,  untuk memastikan skor yang lebih tinggi antara ActivityRank dan Cluster.

### Fitur Tambahan yang Belum ada di Dataset
1. Data jumlah kalori yang dikeluarkan per hari agar seseorang bisa hidup sehat.
2. Goals dari tiap user (apakah olahraga untuk sehat/menurunkan berat badan/alasan lain).
3. Data total steps per hari agar seseorang bisa hidup sehat.

## Feature Encoding
Semua feature sudah di-encode pada tahap feature extraction.

## Data Splitting
Data di split sebelum SelectKBest dan sebelum scaling agar menghindari data leakage.

## Feature Selection
Feature selection dilakukan dengan SelectKBest
![image](https://github.com/user-attachments/assets/5c6da21c-bf92-4137-adb9-04e2ff7df796)

- Hipotesis di section sebelumnya terbukti bahwa Activity Rank itu lebih bermanfaat dibandingkan hanya cluster saja. Maka fitur Cluster bisa di drop.
- Fitur yang diambil adalah fitur dengan Mutual Information Score di atas 0.1 yaitu:
['Total_MET',
 'Avg_METs',
 'TotalDistance',
 'DistancePerStep',
 'TrackerDistance',
 'StepsbyDistance',
 'TotalActiveDistance',
 'TotalSteps',
 'ActiveRatio',
 'AverageActiveMinutes',
 'TotalActiveMinutes',
 'DistanceIntensity',
 'InactiveRatio',
 'SedentaryMinutes',
 'ActivityRank',
 'SedentaryRatio',
 'LightlyActiveMinutes',
 'VeryActiveMinutes',
 'LightActiveDistance',
 'LightlyActiveRatio',
 'AveragePace',
 'ActiveGroup',
 'VeryActiveRatio',
 'VeryActiveDistance',
 'FairlyActiveRatio',
 'ActiveDistanceRatio',
 'FairlyActiveMinutes',
 'TotalUsageMinutes',
 'ModeratelyActiveDistance']

## Feature Transformation
Feature transformation dilakukan dengan StandardScaler karena lebih robust terhadap outliers dan cocok untuk model regression. Sebelumnya, dataset dibagi menjadi train dan test terlebih dahulu.

## Handle Class Imbalance
Tidak dilakukan karena kasus pada dataset ini adalah regression.

## Export Dataframe
- Merge dataset X_train dengan y_train, dan menyimpannya sebagai 'FitbitTrainData.csv'
- Merge dataset X_test  dengan y_test, dan menyimpannya sebagai 'FitbitTestData.csv'















