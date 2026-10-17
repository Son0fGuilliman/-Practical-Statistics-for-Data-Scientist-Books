# Practical Statistics for Data Scientists (O'Reilly) - Code & Concept Reproductions

Repositori ini berisi dokumentasi, penjelasan teori mendalam, dan reproduksi kode lengkap dalam format Jupyter Notebook dari buku **"Practical Statistics for Data Scientists"** (oleh Peter Bruce, Andrew Bruce, & Peter Gedeck, terbitan O'Reilly).

Repositori ini disusun untuk memenuhi tugas akademis serta menjadi referensi praktis penerapan konsep statistik fundamental dalam eksperimentasi Data Science dan pemodelan Machine Learning.

---

## 📁 Struktur Repositori

```
.
├── data/                                 # Seluruh dataset resmi dari repositori buku
│   ├── house_sales.csv
│   ├── loans_income.csv
│   ├── sp500_data.csv.gz
│   ├── web_page_data.csv
│   ├── four_sessions.csv
│   ├── click_rates.csv
│   ├── loan_data.csv.gz                  # Chapter 5 & 6
│   ├── loan3000.csv                      # Chapter 5 & 6
│   ├── loan200.csv                       # Chapter 6
│   └── full_train_set.csv.gz             # Chapter 5
├── PracticalStatisticsChapter1.ipynb    # Chapter 1: Exploratory Data Analysis
├── PracticalStatisticsChapter2.ipynb    # Chapter 2: Data & Sampling Distributions
├── PracticalStatisticsChapter3.ipynb    # Chapter 3: Statistical Experiments & Significance Testing
├── PracticalStatisticsChapter4.ipynb    # Chapter 4: Regression and Prediction
├── PracticalStatisticsChapter5.ipynb    # Chapter 5: Classification
├── PracticalStatisticsChapter6.ipynb    # Chapter 6: Statistical Machine Learning
└── README.md                             # Rangkuman proyek & ringkasan materi
```

## ⚙️ Dependensi

Chapter 1 sampai 4 memakai `pandas`, `numpy`, `scipy`, `statsmodels`, `matplotlib`, dan `seaborn`. Chapter 5 dan 6 menambah beberapa paket berikut:

```bash
pip install scikit-learn statsmodels xgboost imbalanced-learn dmba
```

- `dmba` (paket pendamping buku) dipakai untuk menggambar dan mencetak pohon keputusan. Untuk menggambar pohon, **Graphviz** juga perlu terpasang di sistem (misalnya `sudo apt install graphviz`).
- Versi XGBoost terbaru mewajibkan label numerik dan memakai `iteration_range` (bukan `ntree_limit`). Penyesuaian ini sudah dilakukan dan dijelaskan pada notebook Chapter 6.

---

# 📚 Ringkasan Materi Per Chapter

> Catatan ringkas mengenai konsep-konsep utama dalam statistika, eksperimen, regresi, klasifikasi, dan machine learning.

## Daftar Isi

- [Chapter 1: Exploratory Data Analysis (EDA)](#chapter-1-exploratory-data-analysis-eda)
- [Chapter 2: Data and Sampling Distributions](#chapter-2-data-and-sampling-distributions)
- [Chapter 3: Statistical Experiments and Significance Testing](#chapter-3-statistical-experiments-and-significance-testing)
- [Chapter 4: Regression and Prediction](#chapter-4-regression-and-prediction)
- [Chapter 5: Classification](#chapter-5-classification)
- [Chapter 6: Statistical Machine Learning](#chapter-6-statistical-machine-learning)

---

## Chapter 1: Exploratory Data Analysis (EDA)

### Estimator Lokasi & Variabilitas
- **Ukuran pemusatan data**: Mean, Trimmed Mean, Median.
- **Ukuran penyebaran data**: Standard Deviation, Interquartile Range (IQR), Median Absolute Deviation (MAD).

### Eksplorasi Distribusi Data
- **Visualisasi**: Boxplot, Frequency Table, Histogram, Density Plot.
- **Tujuan**: Mengidentifikasi skewness, kurtosis, dan keberadaan outliers.

### Eksplorasi Data Kategorikal

- **Analisis variabel kualitatif** melalui:
  * Mode
  * Expected Value
  * Bar Chart

### Eksplorasi Multivariat

- **Pemodelan hubungan antarvariabel** menggunakan:
  * Matriks korelasi (Pearson & Spearman)
  * Scatter Plot
  * Hexagonal Binning
  * Contour Plot
  * Violin Plot
  * Cross-Tabulation / Contingency Table

---

## Chapter 2: Data and Sampling Distributions

### Random Sampling & Selection Bias
- **Random Sampling**: Pentingnya penarikan sampel acak untuk menghindari bias sistematis.
- **Selection Bias**: Bias yang muncul jika sampel tidak benar-benar representatif terhadap populasi.

### Central Limit Theorem (CLT) & Standard Error

- **Central Limit Theorem (CLT)**: Distribusi rata-rata sampel (*sample mean*) akan mendekati Distribusi Normal seiring bertambahnya ukuran sampel ($n$), terlepas dari bentuk distribusi populasi aslinya.
- **Standard Error (SE)**: Mengukur variabilitas atau ketidakpastian dari estimasi statistik sampel.
  * Rumus: `SE = s / √n`

### The Bootstrap & Confidence Intervals

- **Bootstrap**: Teknik komputasi berbasis *resampling with replacement* untuk memperkirakan Standard Error dan membangun Confidence Interval (CI) tanpa bergantung pada rumus matematis yang kaku.

### Distribusi Statistik Kunci

- **Normal & QQ-Plot**: Alat uji visual normalitas data.
- **Binomial**: Memodelkan frekuensi sukses dalam $n$ kali percobaan biner (contoh: A/B testing).
- **Poisson & Exponential**: Memodelkan frekuensi kejadian berdurasi serta interval waktu tunggu antarkejadian.

---

## Chapter 3: Statistical Experiments and Significance Testing

### A/B Testing & Permutation Tests

- **A/B Testing**: Eksperimen terkontrol dengan kelompok *treatment* dan *control* untuk mengisolasi hubungan sebab-akibat.
- **Permutation Test**: Pendekatan non-parametrik berbasis pemutaran/pengacakan label data untuk menghitung $p$-value secara empiris tanpa asumsi Distribusi Normal.

### Signifikansi Statistik, p-Values & Errors

- **$p$-Value**: Probabilitas munculnya hasil yang se-ekstrem observasi apabila Hipotesis Nol ($H_0$) dianggap benar.
- **Matriks Error**:
  * **Type I Error**: False Positive, dikendalikan oleh $\alpha$.
  * **Type II Error**: False Negative, dikendalikan oleh Power $= 1 - \beta$.

### ANOVA & Chi-Square Tests

- **ANOVA ($F$-Test)**: Membandingkan rerata dari $>2$ kelompok secara simultan guna mencegah pembengkakan Type I Error (*Alpha Inflation*).
- **Chi-Square ($\chi^2$) Test**: Digunakan untuk menguji independensi dan perbandingan proporsi pada data kategorikal (contoh: Click/No-Click).

### Multi-Arm Bandits & Power Analysis

- **Multi-Arm Bandits**: Mengoptimalkan alokasi trafik secara dinamis selama tes berlangsung untuk meminimalkan kerugian bisnis (*opportunity cost*).
- **Power Analysis**: Digunakan sebelum eksperimen dimulai untuk menentukan ukuran sampel minimum ($n$) berdasarkan Effect Size ($d$), $\alpha$, dan Target Power (80%).

---

## Chapter 4: Regression and Prediction

### Simple & Multiple Linear Regression

- **Model**: Memodelkan hubungan antara variabel prediktor dan variabel target numerik menggunakan *Method of Least Squares* yang meminimalkan Residual Sum of Squares (RSS).
- **Evaluasi performa**:
  * **RMSE**: Mengukur besarnya error prediksi.
  * **$R^2$ / Adjusted $R^2$**: Proporsi varians yang berhasil dijelaskan oleh model.

### Prediction Intervals & Factor Variables

- **Prediction Interval**: Jauh lebih lebar daripada Confidence Interval karena memperhitungkan variabilitas individual di samping ketidakpastian estimasi parameter model.
- **Factor Variables**: Pemodelan variabel kategorikal menggunakan Dummy Variables / Reference Coding untuk mencegah *Dummy Variable Trap*.

### Regression Diagnostics & Multicollinearity

- **Multikolinearitas**: Diukur menggunakan Variance Inflation Factor (VIF) untuk mendeteksi korelasi berlebihan antarprediktor yang mengganggu stabilitas koefisien.
- **Diagnosis Residual**: Evaluasi plot residual untuk mendeteksi:
  * Outliers
  * Influential Values (Cook's Distance)
  * Heteroskedastisitas (varians error tidak konstan)

### Non-Linear Regression

- Mengatasi hubungan non-linear menggunakan **Polynomial Regression**, **Splines (B-Splines)**, dan **Generalized Additive Models (GAM)** untuk menangkap pola kurva yang kompleks secara fleksibel dan stabil.

---

## Chapter 5: Classification

Klasifikasi adalah *supervised learning* untuk memprediksi apakah sebuah record termasuk kelas 1 atau 0 (atau salah satu dari beberapa kategori). Hasil yang lebih berguna daripada label biner adalah **propensity score** (probabilitas keanggotaan kelas), yang diubah menjadi keputusan lewat **cutoff**. Data yang dipakai: pinjaman LendingClub (*paid off* vs *default*).

### Naive Bayes

- **Ide**: Memakai probabilitas bersyarat $P(X_j \mid Y)$ untuk mengestimasi posterior $P(Y \mid X_1,\dots,X_p)$.
- **Asumsi "naive"**: Antarprediktor saling independen jika kelasnya diketahui, sehingga probabilitas bersama cukup dihitung sebagai hasil kali probabilitas individual.
- **Catatan**: Standar hanya untuk prediktor kategorikal; memakai *Laplace smoothing* agar kategori yang tidak pernah muncul tidak menghasilkan probabilitas nol. Estimasi probabilitasnya bias, tetapi baik untuk meranking record.

### Discriminant Analysis (LDA)

- **Ide**: Mencari kombinasi linear prediktor yang memaksimalkan rasio variasi antar-kelompok terhadap variasi dalam-kelompok ($SS_{between}/SS_{within}$), memakai **matriks kovarians**.
- **Varian**: QDA (matriks kovarians berbeda tiap kelompok). Jika prediktor distandardisasi, bobot diskriminan bisa dibaca sebagai kepentingan variabel.

### Logistic Regression & GLM

- **Logit / log-odds**: $\log\text{Odds}(Y=1)=\beta_0+\beta_1x_1+\cdots$, lalu dipetakan kembali ke probabilitas dengan fungsi logistik.
- **Odds ratio**: $e^{\beta_j}$ menyatakan perubahan odds untuk kenaikan satu unit $X_j$ (misal pinjaman usaha kecil memiliki odds default sekitar 3,4 kali pinjaman pelunasan kartu kredit).
- **Fitting**: *Maximum Likelihood Estimation* (bukan least squares), dinilai dengan *deviance*. Regresi logistik adalah kasus khusus **GLM** (family binomial, link logit).
- **Perluasan**: spline/GAM dan analisis partial residual (berbentuk dua awan titik).

### Evaluating Classification Models

- **Confusion matrix** dan turunannya: **Accuracy**, **Precision**, **Recall (Sensitivity)**, **Specificity**.
- **ROC curve & AUC**: trade-off recall dan specificity di semua cutoff; AUC = 0,5 setara tebakan acak, AUC = 1 sempurna (model pinjaman: AUC ≈ 0,69).
- **Lift / Gains chart**: seberapa baik model menemukan kelas langka pada desil teratas dibanding pemilihan acak.
- **Rare class problem**: pada data tidak seimbang, accuracy menyesatkan.

### Strategies for Imbalanced Data

- **Undersampling** (mengurangi kelas dominan) dan **Oversampling** (bootstrap kelas langka).
- **Up/Down Weighting**: bobot $1/p$ pada kelas langka (persentase prediksi default naik dari ±1% menjadi ±61%).
- **Data generation / SMOTE**: membuat record sintetis dari tetangga terdekat.
- **Cost-based classification**: memasukkan biaya false positive dan false negative ke penentuan cutoff.

---

## Chapter 6: Statistical Machine Learning

Metode *supervised* yang digerakkan oleh data (tanpa struktur linear global). Gagasan utamanya adalah **ensemble learning**: memakai banyak model untuk satu prediksi, terutama pada **pohon keputusan**.

### K-Nearest Neighbors (KNN)

- **Ide**: Cari $K$ record paling mirip, lalu ambil kelas mayoritas (klasifikasi) atau rata-rata (regresi).
- **Komponen penting**: *distance metric* (Euclidean, Manhattan, Mahalanobis), *one-hot encoding*, dan **standardisasi** (z-score) agar variabel berskala besar tidak mendominasi.
- **Memilih K**: K kecil menyebabkan overfitting, K besar menyebabkan oversmoothing (*bias-variance trade-off*), dipilih lewat cross-validation.
- **KNN sebagai feature engine**: probabilitas hasil KNN dipakai sebagai fitur untuk model tahap kedua.

### Tree Models

- **Recursive partitioning**: membagi data berulang kali berdasarkan split yang memaksimalkan homogenitas.
- **Impurity**: Gini impurity dan Entropy. Pohon yang tumbuh penuh akan overfit, sehingga dibatasi dengan `max_depth`, `min_samples_split`, `min_impurity_decrease` (dioptimalkan dengan `GridSearchCV`).
- **Kelebihan**: mudah ditafsirkan sebagai aturan if-then; **kekurangan**: kalah akurat dari ensemble.

### Bagging & Random Forest

- **Bagging**: melatih banyak model pada sampel *bootstrap*, lalu merata-ratakannya.
- **Random Forest**: bagging pada pohon, ditambah pengambilan sampel variabel di setiap split.
- **OOB error**: estimasi error dari record yang tidak masuk sampel bootstrap tiap pohon.
- **Variable importance**: penurunan akurasi (permutasi) dan penurunan Gini impurity.
- **Hyperparameter**: `min_samples_leaf` dan `max_leaf_nodes` untuk mencegah overfitting.

### Boosting (XGBoost)

- **Ide**: barisan model, di mana tiap model berikutnya berfokus pada record yang salah/residualnya besar (AdaBoost, Gradient Boosting, Stochastic Gradient Boosting).
- **XGBoost**: implementasi efisien stochastic gradient boosting dengan parameter `learning_rate`, `subsample`, `max_depth`, `n_estimators`.
- **Regularization**: `reg_lambda` (L2) dan `reg_alpha` (L1) menekan overfitting. Pada data pinjaman, model tanpa regularisasi sangat overfit.
- **Cross-validation**: wajib untuk memilih hyperparameter; pohon dangkal dengan learning rate kecil umumnya paling stabil.
