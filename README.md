# Practical Statistics for Data Scientists (O'Reilly) - Code & Concept Reproductions

Repositori ini berisi dokumentasi, penjelasan teori mendalam, dan reproduksi kode lengkap dalam format Jupyter Notebook dari buku **"Practical Statistics for Data Scientists"** (oleh Peter Bruce, Andrew Bruce, & Peter Gedeck, terbitan O'Reilly).

Repositori ini disusun untuk memenuhi tugas akademis serta menjadi referensi praktis penerapan konsep statistik fundamental dalam eksperimentasi Data Science dan pemodelan Machine Learning.

---

## 📁 Struktur Repositori

```text
.
├── data/                                 # Seluruh dataset resmi dari repositori buku
│   ├── house_sales.csv
│   ├── loans_income.csv
│   ├── sp500_data.csv.gz
│   ├── web_page_data.csv
│   ├── four_sessions.csv
│   └── click_rates.csv
├── PracticalStatisticsChapter1.ipynb    # Chapter 1: Exploratory Data Analysis
├── PracticalStatisticsChapter2.ipynb    # Chapter 2: Data & Sampling Distributions
├── PracticalStatisticsChapter3.ipynb    # Chapter 3: Statistical Experiments & Significance Testing
├── PracticalStatisticsChapter4.ipynb    # Chapter 4: Regression and Prediction
└── README.md                             # Rangkuman proyek & ringkasan materi

# 📚 Ringkasan Materi Per Chapter

## Chapter 1: Exploratory Data Analysis (EDA)

### Estimator Lokasi & Variabilitas
- Mengukur pemusatan data menggunakan **Mean**, **Trimmed Mean**, dan **Median**.
- Mengukur penyebaran menggunakan **Standard Deviation**, **Interquartile Range (IQR)**, dan **Median Absolute Deviation (MAD)**.

### Eksplorasi Distribusi Data
- Menggunakan **Boxplot**, **Frequency Table**, **Histogram**, dan **Density Plot** untuk mengidentifikasi **skewness**, **kurtosis**, dan keberadaan **outliers**.

### Eksplorasi Data Kategorikal
- Menganalisis variabel kualitatif melalui **Mode**, **Expected Value**, dan **Bar Chart**.

### Eksplorasi Multivariat
- Memodelkan hubungan antarvariabel menggunakan matriks korelasi (**Pearson** & **Spearman**), **Scatter Plot**, **Hexagonal Binning**, **Contour Plot**, **Violin Plot**, serta **Cross-Tabulation/Contingency Table**.

---

## Chapter 2: Data and Sampling Distributions

### Random Sampling & Selection Bias
- Pentingnya penarikan sampel acak (**Random Sampling**) untuk menghindari bias sistematis (**Selection Bias**) dan memastikan sampel benar-benar representatif terhadap populasi.

### Central Limit Theorem (CLT) & Standard Error
- **CLT**: Menjamin bahwa distribusi rata-rata sampel (*sample mean*) akan selalu mendekati **Distribusi Normal** seiring bertambahnya ukuran sampel ($n$), terlepas dari bentuk distribusi populasi aslinya.
- **Standard Error (SE)**: Mengukur variabilitas atau ketidakpastian dari estimasi statistik sampel ($SE = s / \sqrt{n}$).

### The Bootstrap & Confidence Intervals
- **Bootstrap**: Teknik komputasi berbasis *resampling with replacement* untuk memperkirakan **Standard Error** dan membangun **Confidence Interval (CI)** tanpa harus bergantung pada rumus matematis yang kaku.

### Distribusi Statistik Kunci
- **Normal & QQ-Plot**: Alat uji visual normalitas data.
- **Binomial**: Memodelkan frekuensi sukses dalam $n$ kali percobaan biner (A/B testing).
- **Poisson & Exponential**: Memodelkan frekuensi kejadian berdurasi serta interval waktu tunggu antarkejadian.

---

## Chapter 3: Statistical Experiments and Significance Testing

### A/B Testing & Permutation Tests
- **A/B Testing**: Eksperimen terkontrol dengan kelompok *treatment* dan *control* untuk mengisolasi hubungan sebab-akibat.
- **Permutation Test**: Pendekatan non-parametrik berbasis pemutaran/pengacakan label data untuk menghitung $p$-value secara empiris tanpa asumsi Distribusi Normal.

### Signifikansi Statistik, p-Values & Errors
- **$p$-Value**: Memuat probabilitas munculnya hasil yang se-ekstrem observasi apabila Hipotesis Nol ($H_0$) dianggap benar.
- **Matriks Error**: Mengontrol **Type I Error** (*False Positive*, dikendalikan $\alpha$) dan **Type II Error** (*False Negative*, dikendalikan oleh **Power** $= 1 - \beta$).

### ANOVA & Chi-Square Tests
- **ANOVA** ($F$-Test): Membandingkan rerata dari $>2$ kelompok secara simultan guna mencegah pembengkakan Type I Error (**Alpha Inflation**).
- **Chi-Square** ($\chi^2$) Test: Digunakan untuk menguji independensi dan perbandingan proporsi pada data kategorikal (*Click/No-Click*).

### Multi-Arm Bandits & Power Analysis
- **Multi-Arm Bandits**: Mengoptimalkan alokasi trafik secara dinamis selama tes berlangsung untuk meminimalkan kerugian bisnis (*opportunity cost*).
- **Power Analysis**: Digunakan sebelum eksperimen dimulai untuk menentukan ukuran sampel minimum ($n$) berdasarkan **Effect Size** ($d$), $\alpha$, dan **Target Power** ($80\%$).

---

## Chapter 4: Regression and Prediction

### Simple & Multiple Linear Regression
- Memodelkan hubungan antara variabel prediktor dan variabel target numerik menggunakan **Method of Least Squares** yang meminimalkan **Residual Sum of Squares (RSS)**.
- Evaluasi performa menggunakan **RMSE** (besarnya error prediksi) dan $R^2$ / **Adjusted $R^2$** (proporsi varians yang berhasil dijelaskan oleh model).

### Prediction Intervals & Factor Variables
- **Prediction Interval**: Jauh lebih lebar daripada **Confidence Interval** karena memperhitungkan variabilitas individual di samping ketidakpastian estimasi parameter model.
- **Factor Variables**: Pemodelan variabel kategorikal menggunakan **Dummy Variables** / **Reference Coding** untuk mencegah **Dummy Variable Trap**.

### Regression Diagnostics & Multicollinearity
- **Multikolinearitas**: Diukur menggunakan **Variance Inflation Factor (VIF)** untuk mendeteksi korelasi berlebihan antarprediktor yang mengganggu stabilitas koefisien.
- **Diagnosis Residual**: Evaluasi plot residual untuk mendeteksi **Outliers**, **Influential Values** (**Cook's Distance**), dan **Heteroskedastisitas** (varians error tidak konstan).

### Non-Linear Regression
- Mengatasi hubungan non-linear menggunakan **Polynomial Regression**, **Splines** (**B-Splines**), dan **Generalized Additive Models (GAM)** guna menangkap pola kurva yang kompleks secara fleksibel dan stabil.