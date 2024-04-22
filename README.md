# Supermarket Customers Data Analysis
### Alif Wahyu Syahnanda

- Jupyter notebook: **[SupermarketCustomers_CPM2](https://github.com/awsyahnanda/supermarket-sales-project/blob/main/SupermarketCustomers_CPM2.ipynb)**
- Data set: **[Supermarket Customers.csv](https://drive.google.com/drive/folders/1WodnBbuYTvsF0-6HTuQABQ0KCS31lqbK?usp=sharing)**

# Table of contents
1. [Pendahuluan](#introduction)

2. [Deskripsi dari data set](#section2)
   1. [Statistik Deskriptif](#sec2p1)
   2. [Missing Value dan Outlier](#sec2p2)
   3. [Penambahan Kolom](#sec2p3)

3. [Data Analysis](#section3)
   1. [Uji Normaltest](#sec3p1)
   2. [Uji Korelasi Spearman](#sec3p2)
   3. [Profit Paling Rendah Berdasarkan `Subregion` dan `Product`](#sec3p3)

4. [Kesimpulan Data Analysis](#section4)

5. [Referensi](#section5)
   
  
## 1. Pendahuluan <a name="introduction"></a>
- README ini menjelaskan pekerjaan yang dilakukan pada set data Supermarket Customers. Sumber daya yang digunakan termasuk Python dan paket terkait Jupyter, matplotlib, Seaborn, statsmodels, dan SciPy. Semua paket ini disertakan sebagai bagian dari distribusi Anaconda Python.
- Analisis ini berbentuk satu notebook Jupyter dengan nama file yang diberikan di atas. Untuk melihat file ini, unduh dari repositori ini dan mulai notebook Jupyter di folder yang berisi file tersebut. Gunakan perintah Jupyter notebook pada baris perintah.
- Semua gambar yang dimaksudkan untuk disertakan dalam README ini berada di subdirektori images dari repositori ini.

##  2. Data Understanding dan Cleaning <a name="section2"></a>
Dataset yang disediakan berisi data pelanggan dari perusahaan Supermarket yang bergerak di industri retail pada bidang bisnis ke customer (B2C) . Setiap baris dalam dataset mewakili satu member pelanggan yang terdaftar, dengan total 2.240 pelanggan. Dataset ini terdiri dari berbagai kolom, 
## 2.1 Statistik Deskriptif <a name="sec2p1"></a>
Fungsi **describe()** dari library pandas dapat menunjukkan ringkasan penting tentang statistika deskriptif data set.

foto describe()

**Penjelasan**

Insight :
* Semua pelanggan memiliki ID unik masing-masing (Jumlah Pelanggan = Jumlah Unik di Kolom **ID**)

Berdasarkan data diatas terdapat beberapa hal yang perlu dilakukan perapihan data dan pembersihan data pada beberapa kolom, untuk meningkatkan relevansi data dan keakuratan data yang nantinya akan dilakukan analisis, maka dibawah ini kolom yang perlu ditindak lanjuti di dalam proses *Data Cleaning* :

* Tipe data kolom **Dt_Customer** masih dalam bentuk object harus diubah menjadi datetime. Karena kolom "Dt_Customer" berisi tanggal registrasi pelanggan, maka format tipe datanya adalah tanggal waktu *(datetime)*

* Pada kolom **ID** ada 1 yang memiliki nilai 0 hal tersebut nantinya akan diubah dengan random nilai agar membantu analsis lebih relevan dan real

*  Pada kolom **Marital_Status**, didapati beberapa istilah seperti "Absurd" dan "YOLO" yang tidak relevan pengartiannya dan tidak sesuai dengan klasifikasi status perkawinan. Namun, kita dapat mengasumsikan bahwa individu yang mengisi status perkawinan ini sebenarnya masih Single karena jika mereka memiliki pasangan, mereka dapat menggunakan "Together" (akan diganti dengan "Cohabitation" [referensi](https://en.wikipedia.org/wiki/Cohabitation)) atau "Married". Selain itu, status "Single" dan "Alone" pada dasarnya memiliki arti yang sama, seperti halnya "Divorced" dan "Widow", keduanya mengindikasikan perpisahan. Untuk menyederhanakan analisis dan lebih relevan, kolom baru **"Marital_Status"** akan dibuat, yang hanya terdiri dari **"Single", "Cohabitation", "Married", dan "Divorced"** 

* Pada kolom **Education**, terdapat nilai "2n Cycle" yang menurut salah satu [sumber referensi](https://www.studera.nu/startpage/higher-education-studies/higher-education-in-sweden/study-levels-and-degrees/#:~:text=First%20cycle%20is%20for%20the,offered%20at%20all%20three%20cycles.) berarti gelar Master. Selain itu, pendidikan "Basic" mengacu pada individu yang hanya menyelesaikan pendidikan hingga sekolah menengah atas (SMA) atau memiliki pendidikan informal dan tidak melaksanakan perguruan tinggi menurut [definisi pendidikan dasar](https://uis.unesco.org/en/glossary-term/basic-education). Oleh karena itu, kami akan mengubah isi kolom 'Education', di mana "2n Cycle" akan dikelompokkan sebagai "Master", dan "Basic" akan diidentifikasi sebagai "Non-degree" menurut [referensi](https://dictionary.cambridge.org/dictionary/english/non-graduate). Selain itu, tingkat pendidikan "Graduation" akan diganti dengan "Bachelor" untuk menghindari definisi yang kurang relevan

## 2.2 Missing Value dan Outlier <a name="sec2p2"></a>
Perlu dilakukan pengecekan terhadap `missing value` dan `outlier` dalam data set yang dapat mengganggu analisis data.

Dari data set, tidak ditemukan data NaN atau `missing value` dan tidak ada outlier yang tidak diperlukan dalam analisis, maka tidak dilakukan data cleaning.

## 2.3 Penambahan Kolom <a name="sec2p3"></a>

Selanjutnya, perlu ditambahkan kolom `datetime` pada dataset agar disaat analisis dapat melihat tren dari data. hal ini dilakukan dengan menggunakan kolom `Date Key`.

# 3. Data Analysis <a name="section3"></a>

Setelah melakukan tahap Data Cleaning. Sekarang, data siap untuk dianalisis untuk mencari tahu bagaimana pengaruh `Profit` dengan `Sales`, `Quantity` dan `Discount`. 

## 3.1 Uji Normaltest <a name="sec3p1"></a>

Perlu dilakukan uji normaltest untuk menentukan uji parametrik atau non parametrik yang akan digunakan pada analisis selanjutnya. Berikut adalah hasil dari uji normaltest dari kolom `Sales`, `Quantity`, `Discount` dan `Profit`.

Sales: Statistics=18033.308, p-value=0.000
Sales is not normally distributed (reject H0)

Quantity: Statistics=2148.018, p-value=0.000
Quantity is not normally distributed (reject H0)

Discount: Statistics=2977.822, p-value=0.000
Discount is not normally distributed (reject H0)

Profit: Statistics=14363.736, p-value=0.000
Profit is not normally distributed (reject H0)

Hasil diatas menunjukkan bahwa keempat kolom diatas memiliki data yang tidak terdistribusi normal. Maka, untuk selanjutnya perlu dilakukan uji non-parametrik.

## 3.2 Uji Korelasi Spearman <a name="sec3p2"></a>

Perlu dilakukan uji korelasi antara `Profit` dengan `Sales`, `Quantity` dan `Discount` untuk melihat apakah ada korelasi kuat antara kolom tersebut

Spearman's correlation coefficient antara Sales dan Profit: 0.5184066611400607
Spearman's correlation coefficient antara Quantity dan Profit: 0.2344912031227869
Spearman's correlation coefficient antara Discount dan Profit: -0.5433501822306211

Berdasarkan hasil diatas, 
* antara Sales dan Profit memiliki hubungan yang moderat dan positif,
* antara Quantity dan Profit memiliki hubungan yang lemah dan positif,
* antara Discount dan Profit memiliki hubungan yang moderat dan negatif.

## 3.3 Profit Paling Rendah Berdasarkan `Subregion` dan `Product` <a name="sec3p3"></a>

Berdasarkan hasil analisis, profit paling rendah adalah pada `Subregion` ANZ dan JAPN. sementara pada kedua `Subregion` tersebut `Product` dengan profit paling rendah adalah ContactMatcher. Selanjutnya dilakukan uji korelasi koefisien antara `Profit` dan `Discount` dikalikan dengan `Sales` pada `Subregion` ANZ dan JAPN dengan `Product` ContactMatcher, berikut hasil uji korelasinya.

Spearman's correlation coefficient antara Discount*Sales dan Profit di `Subregion` ANZ: -0.9603105960173816
Spearman's correlation coefficient antara Discount*Sales dan Profit di `Subregion` JAPN: -0.904091425332207

Berdasarkan hasil tersebut, dapat disimpulkan bahwa antara `Profit` dan `Discount` dikalikan dengan `Sales` memiliki korelasi yang sangat kuat dan negatif.

## 4. Kesimpulan Data Analysis <a name="section4"></a>

Kesimpulan utama adalah sebagai berikut
1. `Profit`:
    - Rata-rata: 28.66
    - Standar Deviasi: 234.26
    - Minimum: -6599.98
    - Median: 8.67
    - Maximum: 8399.98
2. `Sales`:
    - Rata-rata: 229.86
    - Standar Deviasi: 623.25
    - Minimum: 0.44
    - Median: 54.49
    - Maximum: 22638.58
3. `Discount`:
    - Rata-rata: 0.16
    - Standar Deviasi: 0.21
    - Minimum: 0.00
    - Median: 0.20
    - Maximum: 0.80
4. Korelasi antara `Profit` dan `Discount` dikalikan dengan `Sales` pada `Subregion` ANZ dan JAPN dengan `Product` ContactMatcher adalah -0.96 pada `Subregion` ANZ dan 0.90 pada `Subregion` JAPN.

## 5. Referensi <a name="section5"></a>

- [1]  Anaconda Distribution
https://www.anaconda.com/

- [2] Python Software Foundation
https://www.python.org/

- [3] Project Jupyter
https://jupyter.org/

- [4] Sharing Jupyter notebooks
https://nbviewer.jupyter.org/

- [5] pandas: Python data analysis library
https://pandas.pydata.org/

- [6] numpy: The fundamental package for scientific computing with Python
https://numpy.org/

- [7] seaborn: statistical data visualization
https://seaborn.pydata.org/index.html#

- [8] matplotlib: Python plotting library
https://matplotlib.org/

- [9] plotly: low-code python data Apps
https://plotly.com/

- [10] Amazon AWS SaaS Sales Dataset
https://www.kaggle.com/datasets/nnthanh101/aws-saas-sales

- [11] IPython
https://ipython.org/

- [12] statsmodels: Statistics in Python
https://www.statsmodels.org/stable/index.html

- [13] scipy.stats : Statistics with SciPy
https://docs.scipy.org/doc/scipy/reference/tutorial/stats.html
