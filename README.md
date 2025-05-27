# Laporan Proyek Machine Learning - Ibnu Raju Humam

[LinkedIn - Ibnu Raju Humam](https://www.linkedin.com/in/ibnu-raju-humam-a14502221/)

## Domain Proyek

Air merupakan kebutuhan dasar manusia yang harus tersedia dalam kondisi bersih, aman, dan layak untuk dikonsumsi dan digunakan dalam kehidupan sehari-hari. Akses terhadap air minum layak merupakan salah satu tujuan dari _Sustaineble Development Goals_ (SDGs) ke-6 yaitu _Clean Water and Sanitation_ [[1]]. Namun, lebih dari dua miliar orang di dunia masih kesulitan mendapatkan air minum yang aman, dan sekitar 3,6 miliar orang tidak memiliki akses terhadap sanitasi air bersih yang memadai [[2]] [[3]]. Air minum yang layak tentunya aman dari patogen, zat kimia berbahaya, serta memiliki rasa dan bau yang dapat diterima [[4]]. Jika manusia meminum air yang tidak layak dapat menyebabkan masalah kesehatan yang serius seperti hepatitis, tifus, diare, kolera, bahkan bisa menjadi penyebab kematian, dan hal ini biasanya terjadi di negara-negara berkembang [[2]] [[4]].

Permasalahan mendapatkan air minum layak bermacam-macam. Dalam [[5]], _literature review_ akses air minum layak dengan relevansi terhadap Jawa Tengah, Indonesia, menunjukkan ketimpangan akses air minum layak antara daerah perkotaan dan pedesaan menjadi salah satu masalah utama, sehingga untuk mencapai tujuan SDGs ke-6 diperlukan upaya dan koordinasi antar pemerintah dan seluruh elemen masyarakat, serta penerapan teknologi inovatif untuk meningkatkan distribusi dan memastikan kelayakan air bersih terjaga dan terpantau. Selain itu juga, kesenjangan sosial dan ekonomi menentukan kondisi kemudahan akses air layak minum dan bersih [[6]]. Informasi dari GoodStats berdasarkan sumber dari Food and Agriculture Organization (FAO), menunjukkan bahwa Indonesia berada pada urutan ketujuh dari sebelas negara di ASEAN dengan air minum layak [[7]].

Selain peningkatan layanan dan infrastruktur, upaya penilaian kelayakan air juga penting  dilakukan untuk memastikan apakah air dapat dikonsumsi dengan aman atau tidak. Salah satu pendekatan yang dapat digunakan yakni menggunakan pendekatan Machine Learning (ML). Penelitian oleh [[8]], yang menggunakan pendekatan _machine learning_ juga, menggunakan Random Forest (RF) dan Support Vector Machine (SVM) mampu memprediksi kelayakan air minum, dengan hasil akurasi terbaik sebesar 69.20% menggunakan Random Forest. Dengan begitu proyek ini bertujuan untuk mengembangkan model prediksi kelayakan air minum dengan memanfaatkan _dataset_ [Water Quality] dari Kaggle. Beberapa algoritma yang digunakan dalam proyek ini adalah K-Nearest Neighbors (KNN), Support Vector Machine (SVM), Random Forest (RF), dan Gradient Boosting (GB). Model akan dievaluasi menggunakan matriks evaluasi yaitu _accuracy_, _precision_, _recall_, dan _F1-Score_, guna mengetahui algoritma yang paling optimal dalam memprediksi air layak minum.

## Business Understanding
### Problem Statements
1. Pernyataan Masalah Ke-1
Masih banyak masyarakat di dunia, termasuk di Indonesia, yang belum memiliki akses mudah mendapatkan air minum yang layak. Beberapa faktor yang menyebabkan hal tersebut yaitu infrastruktur yang belum merata di setiap daerah, layanan air yang sulit diakses, dan juga proses identifikasi kelayakan air minum yang digunakan untuk menilai apakah air berpotensi membahayakan kesehatan atau tidak.
2. Pernyataan Masalah Ke-2
Masih minimnya ketersediaan sistem prediksi berbasis data yang dapat mengklasifikasikan apakah air dapat dikonsumsi secara aman atau tidak. Dalam penilaian kelayakan ini perlu menggunakan indikator kualitas air yang terukur dan dapat dianalisis, sehingga proses lasifikasikan dapat dilakukan, misal dengan ML.
3. Pernyataan Masalah Ke-3
Diperlukan metode yang efektif dan efisien untuk membantu proses validasi kelayakan air minum. Proses ini tentu untuk mengetahui dengan akurat apakah air yang akan dikonsumsi aman. Dengan metode yang efektif dalam mengenal kelayakan air minum, maka masyarakat dapat menentukan tindakan selanjutnya, yakni menggunakan air tersebut atau perlu mendapatkan perlakukan tertentu.


### Goals
1.	Menjawab Pernyataan Masalah Ke-1
Menggambarkan pentingnya solusi dengan teknologi untuk membantu kemudahan akses air minum yang layak. Dengan teknologi selain memudahkan akses layanan melalui infrastruktur yang memadai, proses penilaian kelayakan air minum juga dapat dikembangkan sehingga kualitas air dapat dikenali.
2.	Menjawab Pernyataan Masalah Ke-2
Mengembangkan sistem klasifikasi berbasis ML yang mampu memprediksi kelayakan air minum dengan parameter-parameter kualitas air yang terukur. Dengan sistem ini proses identifikasi menjadi terbantu dan mudah.
3.	Menjawab Pernyataan Masalah Ke-3
Menyediakan metode prediksi yang akurat berbasis ML, sehingga masyarakat dan pemangku kepentingan lainnya dapat dengan mudah menentukan tingkat keamanan air untuk dikonsumsi.

### Solution Statements
1.	Solusi 1
Menerapkan beberapa algoritma ML untuk prediksi air minum layak seperti K-Nearest Neighbors (KNN), Support Vector Machine (SVM), Random Forest (RF), dan Gradient Boosting (GB).
2.	Solusi 2
Melakukan _hyperparameter tuning_ pada setiap model untuk meningkatkan hasil performa klasifikasi pada matriks evaluasi, menggunakan teknik Bayesian Optimization.
3.	Solusi 3
Mengevaluasi performa setiap model menggunakan matriks yang terukur seperti _accuracy_, _precision_, _recall_, dan _F1-Score_, untuk memilh model terbaik dalam kasus klasifikasi air minum layak menggunakan _dataset_ proyek ini.

## Data Understanding
_Dataset_ yang digunakan dalam proyek ini adalah [Water Quality] yang tersedia secara publik di Kaggle. _Dataset_ ini berisi data hasil pengukuran berbagai parameter kualitas air, yang dapat digunakan untuk memprediksi apakah air tersebut layak dikonsumsi atau tidak. _Dataset_ ini relevan digunakan untuk mengembangkan model klasifikasi berbasis ML karena menyediakan beberapa indikator penting yang dapat berkontribusi terhadap kelayakan air.

Deskripsi Variabel [[9]]:
1.	pH value
Mengukur tingkat keasaman air. Nilai pH berkisar antara 0 hingga 14, dengan nilai netral 7. Nilai pH yang terlalu rendah menunjukkan air yang bersifat asam, sedangkan nilai yang terlalu tinggi menunjukkan sifat basa. Keduanya bisa diindikasikan tidak layak untuk dikonsumsi. 
2.	Hardness
Mengukur jumlah ion kalsium dan magnesium dalam air (mg/L). Kadar hardness yang tinggi dapat mempengaruhi rasa dan menyebabkan endapan pada air.
3.	Solids (Total dissolved solids-TDS)
Total zat padat yang terlarut dalam air (ppm). Indikator ini juga yang mempengaruhi rasa dan kejernihan air. Parameter ini penting digunakan, yang mana air dengan TDS tinggi mengindikasikan zat padat yang terlarut banyak. Nilai TDS yang ideal berkisar antara 500 mg/L hingga maksimum 1000 mg/L untuk tujuan dikonsumsi.
4.	Chloramines
Senyawa ini digunakan sebagai disinfektan dalam pengelolaan air (ppm). Kadar yang terlalu tinggi dari senyawa ini dapat berbahaya bagi kesehatan. Kadar aman dari senyawa ini yaitu maksimal 4 ppm, aman untuk air layak minum.
5.	Sulfate
Kandungan sulfat dalam air (mg/L). Kandungan sulfat yang tinggi dapat menyebabkan masalah kesehatan.
6.	Conductivity
Mengukur kemampuan air untuk menghantarkan aliran listrik. Nilai ini berkaitan dengan kandungan jumlah ion terlarut dalam air.
7.	Organic_carbon
Kandungan karbon organik dalam air (ppm), yang berasal dari materi organik seperti daun, tanaman, atau hewan yang membusuk.
8.	Trihalomethanes
Senyawa kimia yang terbentuk saat klorin bereaksi dengan zat organik dalam air. Terdapat beberapa jenis yang bersifat karsinogenik. Tingkat aman dari parameter ini pada air yakni 80 ppm.
9.	Turbidity
Ukuran kejernihan air (NTU). Air yang keruh biasanya tidak layak untuk dikonsumsi.
10.	Potability
Label yang menunjukkan apakah air aman untuk dikonsumsi (1) atau tidak (0).

### Exploratory Data Analysis (EDA)
- Informasi Struktur Data
    Untuk mengelola data diperlukan pemahaman terkait data yang akan digunakan. _Dataset_ terdiri dari 3.276 baris data, dan semua fitur bertipe numerik, dengan tipe `float64` sebanyak 9 fitur dan `int64` pada kolom target ‘Potability’. Kemudian, dilakukan juga analisis statistik deskriptif untuk melihat rentang, rata-rata, standar deviasi, nilai minimum dan maksimum dari setiap fitur.
    ```sh
    data.info()
    ```
    | No | Kolom             | Non-Null Count | Dtype   |
    |----|-------------------|----------------|---------|
    | 0  | ph                | 2785           | float64 |
    | 1  | Hardness          | 3276           | float64 |
    | 2  | Solids            | 3276           | float64 |
    | 3  | Chloramines       | 3276           | float64 |
    | 4  | Sulfate           | 2495           | float64 |
    | 5  | Conductivity      | 3276           | float64 |
    | 6  | Organic_carbon    | 3276           | float64 |
    | 7  | Trihalomethanes   | 3114           | float64 |
    | 8  | Turbidity         | 3276           | float64 |
    | 9  | Potability        | 3276           | int64   |

    ```sh
    data.describe()
    ```
    | Statistik | ph     | Hardness | Solids   | ... | Potability |
    |-----------|--------|----------|----------|-----|------------|
    | count     | 2785.0 | 3276.0   | 3276.0   | ... | 3276.0     |
    | mean      | 7.08   | 196.37   | 22014.09 | ... | 0.39       |
    | std       | 1.59   | 32.88    | 8768.57  | ... | 0.49       |
    | min       | 0.00   | 47.43    | 320.94   | ... | 0.00       |
    | 25%       | 6.09   | 176.85   | 15666.69 | ... | 0.00       |
    | 50%       | 7.04   | 196.97   | 20927.83 | ... | 0.00       |
    | 75%       | 8.06   | 216.67   | 27332.76 | ... | 1.00       |
    | max       | 14.00  | 323.12   | 61227.20 | ... | 1.00       |

-	Pemeriksaan Missing Values
    Beberapa fitur memiliki missing value
    - pH sebanyak 491
    - Sulfate sebanyak 781
    - Trihalomethanes sebanyak 162
    
    Nilai-nilai ini kemudian akan ditangani dengan teknik imputasi pada tahap _preprocessing_.

-	Distribusi Data
    Visualisasi histogram dilakukan untuk mengevaluasi distribusi tiap fitur dan mengenali data apakah terdistribusi normal atau tidak. Sebagian besar fitur menunjukkan distribusi normal, meskipun ada beberapa yang sedikit _skewed_.
    ![Distribusi Data](https://drive.google.com/uc?export=view&id=1lhAw3zm9Djl94iESPBBahUE0QFxUjX96)

-	Korelasi antar Variabel
    Analisis korelasi menggunakan _heatmap_ dilakukan untuk mengetahui hubungan antar fitur. Hasil menunjukkan bahwa tidak ada fitur tunggal yang sangat dominan, sehingga semua fitur relevan untuk digunakan dalam model.
    ![Heatmap Korelasi](https://drive.google.com/uc?export=view&id=1JWcyekmZpRIdD0-NPIXkLUaw7KfijEu7)

-	Distribusi Variabel Target
    Visualisasi sebaran variabel target membantu untuk memutuskan melakukan penyeimbangan data atau tidak. Distribusi target potability menunjukkan adanya ketidakseimbangan kelas.
    - Kelas 0 (tidak layak): 1998 data
    - Kelas 1 (layak): 1278 data
    
    Distribusi ini menandakan adanya imbalance, sehingga perlu dilakukan _balancing data_, yang akan dilakukan pada tahap _preprocessing_.
 	
    ![Distribusi Variabel Target](https://imgur.com/a/GPOWpkh)

-	Boxplot Fitur terhadap Target
    Visualisasi boxplot bertujuan untuk melihat distribusi setiap fitur terhadap target serta mengidentifikasi _outlier_. Sebagian fitur memiliki _outlier_ yang perlu ditangani dalam proses kali ini.
    ![Boxplot Fitur](https://drive.google.com/uc?export=view&id=1HlDh_1t5ZYYGvxSzgR73nKTEI8Ay-Thk)

## Data Preparation
Tahapan data preparation atau _preprocessing_ dilakukan untuk memastikan data yang akan digunakan selama proses pelatihan model ML berada dalam kondisi optimal, tidak ada _noise_, konsisten, serta memenuhi keperluan yang dibutuhkan oleh model. Adapun yang dilakukan pada proyek ini adalah sebagai berikut:

1.	Penanganan Mission Values
    Seperti yang telah diidentifikasi pada tahapan EDA, terdapat beberapa fitur yang memiliki missing values, yaitu:
    - ph: 491
    - Sulfate: 781
    - Trihalomethanes: 162
    
    Missing values pada fitur-fitur ini ditangani dengan metode imputasi `mean`, karena distribusi data yang relatif simetris, sehingga `mean` menjadi representasi pusat data yang cukup akurat dibanding `median`. Imputasi diperlukan agar model ML tidak gagal dalam membaca data dan tetap bisa melakukan _training_ maupun _testing_ secara lengkap, tanpa nilai yang kosong (NaN).

2.	Penanganan Outlier
    Berdasarkan hasil analisis EDA berupa boxplot, ditemukan _outlier_ pada data, sehingga penanganan _outlier_ perlu dilakukan. Alasannya untuk mengurangi pengaruh nilai ekstrim yang bisa menyebabkan bias pada model, terutama algoritma yang sensitif terhadap skala, seperti KNN. Oleh karena itu, _outlier_ akan langsung dihapus dari _dataset_. Strategi ini dipilih sebab jumlah data yang tersedia masih mewakilkan data sebenarnya.

3.	Penyeimbangan Data
    Distribusi target 'Potability' tidak seimbang (setelah melewati tahap Penanganan Outlier)
    - Tidak Layak (0): 1671
    - Layak (1): 995
    
    Model klasifikasi yang dilatih pada data tidak seimbang cenderung bias terhadap kelas minoritas. Sehingga diperlukan teknik penyeimbangan kelas agar model belajar lebih adil terhadap kedua kelas. Teknik yang digunakan dalam proyek ini yakni **Synthetic Minority Over-sampling Technique** atau **SMOTE**, untuk menyeimbangkan jumlah kelas minoritas dengan membuat data sintetis baru.

4.	Pembagian _Dataset_
    _Dataset_ dibagi menjadi dua bagian:
    - _Training set_ (80%)
    - _Testing set_ (20%)
    
    Pembagian dilakukan dengan `stratification` terhadap label 'Potability'. `Stratification` dilakukan untuk memastikan bahwa distribusi kelas pada _training set_ dan _testing set_ tetap seimbang. Penting dilakukan agar evaluasi model tidak bias.

5.	Feature Scaling
    Semua fitur numerik distandarisasi menggunakan `StandardScaler` dari `Scikit-Learn`, yang mengubah fitur menjadi distribusi normal dengan rata-rata 0 dan standar deviasi 1. Scaling dilakukan setelah Pembagian _Dataset_ agar tidak terjadi _data leakage_ atau kebocoran data dari _training set_ ke _testing set_. Beberapa algoritma yang memerlukan scaling dalam proyek ini seperti KNN, SVM, dan GB, yang sensitif terhadap skala fitur. Dengan standarisasi, semua fitur diperlakukan dengan bobot yang setara untuk mencegah dominasi dari fitur tertentu.

## Modeling
Tahapan pemodelan merupakan inti dari proses analisis prediktif, di mana pada tahapan ini setiap model dilatih dan diuji untuk menyelesaikan masalah kelayakan air minum (Potability). Proses modeling dilakukan dalam dua tahap:
1.	Baseline Modeling: menggunakan parameter default
2.	Model Improvement: dengan hyperparameter tuning menggunakan BayesSearchCV

### 1.	Baseline Modeling (Default Parameters)
#### K-Nearest Neighbors (KNN)
Kelebihan:
-	Sederhana dan tidak memerlukan pelatihan secara eksplisit (lazy learner)
-	Lebih cocok untuk masalah klasifikasi multi kelas

Kekurangan:
-	Sensitif terhadap outlier dan skala fitur
-	Waktu prediksi lambat pada _dataset_ besar karena harus menghitung jarak ke semua titik

Parameter:
-	`n_neighbors=5`: menggunakan 5 tetangga terdekat
-	`weights='uniform'`: semua tetangga diberi bobot yang sama
-	`p=2`: menggunakan Euclidean distance

#### Suport Vector Machine (SVM)
Kelebihan:
-	Efektif dalam ruang berdimensi tinggi
-	Masih efektif meskipun jumlah fitur lebih besar dari jumlah sampel

Kekurangan:
-	Memerlukan _tuning parameter_ yang tepat (seperti C, gamma, dan kernel).
-	Sulit diinterpretasikan.

Parameter:
-	`C=1.0`: regularisasi default
-	`kernel='rbf'`: fungsi kernel radial basis (non-linear)
-	`gamma='scale'`: otomatis menghitung gamma berdasarkan fitur

#### Random Forest
Kelebihan:
-	Dapat menangani data non-linear dan fitur dalam jumlah besar.
-	Lebih tahan terhadap _overfitting_ dibanding single Decision Tree.

Kekurangan:
-	Kurang dapat diinterpretasi.
-	Waktu pelatihan relatif lebih lama.

Parameter:
-	`n_estimators=100`: Jumlah pohon default.
-	`max_depth=None`: Tanpa batas kedalaman pohon
-	`min_samples_split=2`: Minimum jumlah sampel untuk melakukan split internal node
-	`criterion='gini'`: mengukur kualitas split dengan Gini impurity.

#### Gradient Boosting
Kelebihan:
-	Akurasi tinggi, bekerja baik pada data kompleks.
-	Menangani _imbalance class_ dengan baik.

Kekurangan:
-	Rentan terhadap _overfitting_.
-	Pelatihan lebih lambat dibanding RF.

Parameter:
-	`n_estimators=100`: Jumlah boosting stage
-	`learning_rate=0.1`: Kecepatan belajar model.
-	`max_depth=3`: Kedalaman pohon default cukup dangkal
-	`min_samples_split=2`: Minimum jumlah sampel untuk membuat split.
-	`min_samples_leaf=1`: Minimum jumlah sampel yang diperlukan pada daun pohon.
-	`subsample=1.0`: Proporsi data yang digunakan untuk melatih tiap pohon
-	`max_features=None`: Semua fitur digunakan untuk membangun setiap pohon

### 2.	Hyperparameter Tuning
Untuk meningkatkan performa model, dilakukan _hyperparameter tuning_ dengan menggunakan **Bayesian Optimization** melalui `BayesSearchCV` dari library `scikit-optimize`.
Proses ini bertujuan untuk menemukan kombinasi parameter terbaik yang menghasilkan performa optimal dan terbaik. Berikut ruang pencarian parameter yang digunakan dan kombinasi parameter yang dihasilkan dari tahap ini sebagai berikut:
- KNN: `n_neighbors=14`, `weights=distance`, `p=1`
- SVM: `C=6.345403458634548`, `kernel='rbf'`, `gamma=0.1`
- Random Forest: `n_estimators=273`, `max_depth=47`, `min_samples_split=3`, `criterion='gini'`
- Gradient Boosting: `n_estimators=500`, `learning_rate=0.020991852672928267`, `max_depth=10`, `min_samples_split=2`, `min_samples_leaf=1`, `subsample=0.8837767371576486`, `max_features='log2'`

Selanjutnya, kombinasi nilai parameter akan diimplementasikan pada setiap algoritma untuk untuk melatih ulang model. Hasil evaluasi model sebelum dan sesudah _hyperparameter tuning_ akan dijelaskan lebih lanjut pada bagian **Evaluation**.

## Evaluation
Karena permasalahan ini adalah klasifikasi biner (potable vs non potable), maka metrik yang digunakan adalah:
-	_Accuracy_: Proporsi prediksi yang benar terhadap total data.
    $$Accuracy = \frac{TP + TN}{TP + TN + FP + FN}$$
-	_Precision_: Kemampuan model dalam menghindari false positive.
    $$Precision = \frac{TP}{TP + FP}$$
-	_Recall_: Kemampuan model dalam menangkap seluruh positif (layak minum) yang benar.
    $$Recall = \frac{TP}{TP + FN}$$
-	_F1-Score_: Harmonik rata-rata antara _precision_ dan _recall_. Cocok untuk kasus data yang tidak seimbang.
    $$F1 = 2 \cdot \frac{Precision \cdot Recall}{Precision + Recall}$$

### Hasil Evaluasi
#### 1. Baseline Model (Default Parameters)
| Model | Accuracy | Precision | Recall | F1-Score |
| ----- | -------- | --------- | ------ | -------- |
| KNN   | 0.6502   | 0.6220    | 0.7635 | 0.6855   |
| SVM   | 0.6667   | 0.6434    | 0.7455 | 0.6907   |
| RF    | 0.6891   | 0.6944    | 0.6737 | 0.6839   |
| GB    | 0.6368   | 0.6207    | 0.7006 | 0.6582   |

#### 2. Model Improvement (Hyperparameter Tuning)
| Model | Accuracy   | Precision  | Recall     | F1-Score   |
| ----- | ---------- | ---------- | ---------- | ---------- |
| KNN   | 0.6712     | 0.6338     | 0.8084     | 0.7105     |
| SVM   | 0.6726     | 0.6434     | 0.7725     | 0.7020     |
| RF    | 0.7115     | 0.7043     | 0.7275     | 0.7158     |
| GB    | **0.7160** | **0.7069** | **0.7365** | **0.7214** |

### Analisis Hasil
-	Semua model mengalami peningkatan performa setelah dilakukan _hyperparameter tuning_ menggunakan `BayesSearchCV`, baik dari segi _accuracy_, _precision_, _recall_, maupun _F1-Score_.
-	Model Gradient Boosting (GB) memberikan hasil terbaik di seluruh metrik setelah _tuning_, dengan _F1-Score_ tertinggi (0.7214), menunjukkan keseimbangan yang sangat baik antara _precision_ dan _recall_.
-	Random Forest (RF) juga menunjukkan performa tinggi, namun sedikit di bawah GB.
-	Meskipun KNN dan SVM mengalami peningkatan, performa mereka masih di bawah dua model ensemble (RF dan GB).

### Model Terbaik
Berdasarkan hasil evaluasi, model terbaik yang dipilih adalah **Gradient Boosting** karena:
- Memberikan **_F1-Score_ tertinggi** sebesar 0.7214.
- Memiliki **keseimbangan yang baik antara _precision_** (0.7069) **dan _recall_** (0.7365).
- **Cocok untuk _dataset_ dengan potensi _imbalance class_**, serta unggul dalam menangkap pola kompleks dari data.

Model ini direkomendasikan sebagai solusi akhir untuk prediksi kelayakan air minum karena konsistensinya di seluruh metrik evaluasi.


## References
[[1]] “Sustainable Development Goals,” Department of Economic and Social Affairs. Accessed: May 23, 2023. [Online]. Available: https://sdgs.un.org/goals

[[2]] N. Pichel, M. Vivar, M. Fuentes, and M. Fuentes, “The problem of drinking water access: A review of disinfection technologies with an emphasis on solar treatment methods.,” Chemosphere, vol. 218, pp. 1014–1030, 2019, doi: 10.1016/j.chemosphere.2018.11.205.

[[3]] S. Dutta, S. Fajal, and S. Ghosh, “Heavy Metal-Based Toxic Oxo-Pollutants Sequestration by Advanced Functional Porous Materials for Safe Drinking Water.,” Acc. Chem. Res., 2024, doi: 10.1021/acs.accounts.4c00348.

[[4]] M. Pal, Y. Ayele, A. Hadush, S. Panigrahi, and V. Jadhav, “Public Health Hazards Due to Unsafe Drinking Water,” vol. 7, pp. 1–6, 2018, doi: 10.4172/2167-7719.1000138.

[[5]] H. Ramadhan and Bramastia, “KAJIAN SISTEMATIS AKSES AIR MINUM LAYAK DALAM IMPLEMENTASI SDGs AIR BERSIH DAN SANITASI LAYAK DI JAWA TENGAH,” EnviroScienteae, vol. 21, no. 1, pp. 27–33, 2025, doi: http://dx.doi.org/10.20527/es.v21i1.21200.

[[6]] S. Glade and I. Ray, “Safe drinking water for small low-income communities: the long road from violation to remediation,” Environ. Res. Lett., vol. 17, 2022, doi: 10.1088/1748-9326/ac58aa.

[[7]] S. Rahmatillah, “Kelayakan Akses Air Minum dan Sanitasi di Negara-Negara ASEAN,” GoodStats. Accessed: May 23, 2025. [Online]. Available: https://data.goodstats.id/statistic/kelayakan-akses-air-minum-dan-sanitasi-di-negara-negara-asean-wUWP6

[[8]] S. B. Patel, K. Shah, S. Vaghela, M. Aglodiya, and R. Bhattad, “Water Potability Prediction using Machine Learning,” Int. Res. J. Mod. Eng. Technol. Sci., vol. 5, no. 8, pp. 2779–2782, Sep. 2023, doi: 10.56726/IRJMETS44413.

[[9]] A. Kadiwal, “Water Quality,” kaggle. Accessed: May 24, 2024. [Online]. Available: https://www.kaggle.com/datasets/adityakadiwal/water-potability/data

   [1]: <https://sdgs.un.org/goals>
   [2]: <https://www.sciencedirect.com/science/article/abs/pii/S0045653518323129>
   [3]: <https://pubs.acs.org/doi/abs/10.1021/acs.accounts.4c00348>
   [4]: <https://www.researchgate.net/profile/Yodit-Ayele/publication/337673662_Public_Health_Hazards_Due_to_Unsafe_Drinking_Water/links/5de4da80299bf10bc33773b6/Public-Health-Hazards-Due-to-Unsafe-Drinking-Water.pdf>
   [5]: <https://ppjp.ulm.ac.id/journal/index.php/es/article/view/21200>
   [6]: <https://iopscience.iop.org/article/10.1088/1748-9326/ac58aa>
   [7]: <https://data.goodstats.id/statistic/kelayakan-akses-air-minum-dan-sanitasi-di-negara-negara-asean-wUWP6>
   [8]: <https://www.researchsquare.com/article/rs-2965961/v1>
   [9]: <https://www.kaggle.com/datasets/adityakadiwal/water-potability/data>
   [Water Quality]: <https://www.kaggle.com/datasets/adityakadiwal/water-potability/data>
   
