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

Kalori pengguna terbakar lebih banyak mulai jam 6 pagi dan mulai menurut setelah jam 6 sore. Kemungkinan pengguna lebih aktif dari jam 6 pagi hingga 6 sore setiap hari karena orang biasanya sedang bekerja atau belajar selama rentang waktu tersebut.

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

