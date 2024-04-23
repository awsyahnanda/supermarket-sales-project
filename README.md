# Supermarket Customers Data Analysis
### Alif Wahyu Syahnanda

Disclaimer - Harap Membuka DASHBOARD hanya melalui link dibawah ini !
- Jupyter notebook: **[SupermarketCustomers_CPM2](https://github.com/awsyahnanda/supermarket-sales-project/blob/main/SupermarketCustomers_CPM2.ipynb)**
- Data set: **[Supermarket Customers.csv](https://drive.google.com/drive/folders/1WodnBbuYTvsF0-6HTuQABQ0KCS31lqbK?usp=sharing)**
- Dashboard : [**Supermarket Customers Dashboard**](https://public.tableau.com/app/profile/alif.wahyu.syahnanda/viz/SupermarketCustomersDashboard/Dashboard1)

# Table of contents
1. [Pendahuluan](#introduction)
   1. [Latar Belakang](#intro)
   2. [Rumusan Masalah](#introp1)
   3. [Batasan Masalah](#introp2)
   
2. [Data Understanding](#section2)
   1. [Data Overall dan Types](#sec2p1)
   2. [Missing Value dan Duplicate Value](#sec2p2)
   
3. [Exploratory Data Understanding (EDU)](#edu)
   1. [Numerik & Deskriptif](#edu1)
   2. [Kategorik & Deskriptif](#edu2)

4. [Data Cleaning & Feature Engineering](dclean)
   1. [Ringkasan Data Cleaning](dclean1)
  
5. [Data Analysis](#section3)
 
6. [Kesimpulan dan Rekomendasi](#section4)

7. [Referensi](#section5)
   
  
## 1. **Pendahuluan** <a name="introduction"></a>

- README ini menjelaskan pekerjaan yang dilakukan pada set data Supermarket Customers. Sumber daya yang digunakan termasuk Python dan paket terkait Jupyter, matplotlib, Seaborn, statsmodels, dan SciPy. Semua paket ini disertakan sebagai bagian dari distribusi Anaconda Python.
- Analisis ini berbentuk satu notebook Jupyter dengan nama file yang diberikan di atas. Untuk melihat file ini, unduh dari repositori ini dan mulai notebook Jupyter di folder yang berisi file tersebut. Gunakan perintah Jupyter notebook pada baris perintah.
- Semua gambar yang dimaksudkan untuk disertakan dalam README ini berada di subdirektori images dari repositori ini.

### 1.1 Latar Belakang <a name="intro"></a>
Di era pasar industri retail yang sangat dinamis saat ini terdapat keanekaragaman proses pasar dan jual beli yang cukup tidak menentu. Mungkin salah satunya pada industri retail supermarket. Kebutuhan pokok menjadi yang utama dari yang lain untuk memenuhi asupan dan gizi masyarakat. Dengan adanya supermarket cukup memberikan kemudahan dalam mengakses kebutuhan pokok yang dibutuhkan sehari-hari untuk menunjang seluruh aspek perputaran industri dan pasar. Di era yang cukup mengalami perkembangan yang pesat dalam sisi ekonomi, pendidikan, budaya hingga teknologi, justru kebutuhan mendasar sangat menjadi prioritas untuk masyarakat.

Dengan tingginya kebutuhan dan kepentingan dasar tersebut, supermarket adalah pilihan pertama untuk tempat dimana masyarakat mengkases dan mendapatkan suplai kebutuhan sehari-hari. Namun hal tersebut juga harus ditunjang dengan kemampuan dan keterjangkauan dari perusahaan supermarket itu sendiri. Karena masyarakat kian hari memiliki komparasi dan preferensi yang cukup dinamis. Seperti bagaimana mereka dan dimana mereka ingin menggunakan supermarket pilihannya menjadi supplier kebutuhan pokok sehari-hari mereka.

Maka dari itu, perusahaan supermarket perlu menjaga pelayanan yang prima, meningkatkan produk, mengembangkan tawaran-tawaran menarik dan juga melihat kebiasaan dari pelanggan agar masyarakat yang menjadi pelanggan setia tetap percaya serta masyarakat yang menjadi pelanggan baru semakin senang dan puas berbelanja di supermarket pilihannya. Salah satu cara perusahaan dapat melakukannya yaitu dengan melakukan analisa data pelanggan supermarket yang dimiliki. Harapannya dapat membantu perusahaan mengetahui pelanggan mana yang perlu dijaga, ditingkatkan, dan dirayu untuk tetap konsisten berbelanja di supermarket.

### 1.2 Rumusan Masalah <a name="introp1"></a>
Rumusan masalah yang dibahas dalam proses analisis ini digunakan agar analisa dapat terarah dan fokus sehingga didapatkan hasil sesuai yang diharapkan. Rumusan masalah analisis ini adalah sebagai berikut:
1. Bagaimana segmentasi pelanggan berdasarkan kebiasaan mereka melakukan pembelian (recency), frekuensi, dan keuangan (monetary)? (Metode RFM)
2. Dimana saluran transaksi paling banyak pelanggan supermarket sering melakukan pembelian kebutuhan mereka?
3. Produk apa yang paling diminati untuk kebutuhan mereka?
4. Apakah promosi yang sudah dilakukan efektif ?

### 1.3 Batasan Masalah <a name="introp2"></a>
* Menggunakan data pelanggan supermarket dari Juli 2012 hingga Juni 2014
* Perhitungan usia dari tahun terakhir pelanggan bergabung menjadi anggota/member supermarket
* Data penunjang ditambahkan dari referensi internet
  
##  2. **Data Understanding** <a name="section2"></a>
Dataset yang disediakan berisi data pelanggan dari perusahaan Supermarket yang bergerak di industri retail pada bidang bisnis ke customer (B2C) . Setiap baris dalam dataset mewakili satu member pelanggan yang terdaftar, dengan total 2.240 pelanggan. Dataset ini terdiri dari 32 kolom dan 2240 baris.
**Pustaka Penjelasan Kolom Data *Supermarket Customers***

| Category          | Field               | Description                                                             |
|-------------------|---------------------|----------------------------------------------------------               |
| **People**        | ID                  | Customer's unique identifier                                            |
|                   | Year_Birth          | Customer's birth year                                                   |
|                   | Education           | Customer's education level                                              |
|                   | Marital_Status      | Customer's marital status                                               |
|                   | Income              | Customer's yearly household income (Dollar)                             |
|                   | Kidhome             | Number of children in customer's household                              |
|                   | Teenhome            | Number of teenagers in customer's household                             |
|                   | Dt_Customer         | Date of customer's enrollment with the company                          |
|                   | Recency             | Number of days since customer's last purchase (Days)                    |
|                   | Complain            | 1 if the customer complained in the last 2 years, 0 otherwise           |
|-------------------|---------------------|----------------------------------------------------------               |
| **Products**      | MntWines            | Amount spent on wine in the last 2 years (Dollar)                       |
|                   | MntFruits           | Amount spent on fruits in the last 2 years (Dollar)                     |
|                   | MntMeatProducts     | Amount spent on meat in the last 2 years (Dollar)                       |
|                   | MntFishProducts     | Amount spent on fish in the last 2 years (Dollar)                       |
|                   | MntSweetProducts    | Amount spent on sweets in the last 2 years (Dollar)                     |
|                   | MntGoldProds        | Amount spent on gold in the last 2 years (Dollar)                       |
|-------------------|---------------------|----------------------------------------------------------               |
| **Promotion**     | NumDealsPurchases   | Number of purchases made with a discount                                |
|                   | AcceptedCmp1        | 1 if the customer accepted the offer in the 1st campaign, 0 otherwise   |
|                   | AcceptedCmp2        | 1 if the customer accepted the offer in the 2nd campaign, 0 otherwise   |
|                   | AcceptedCmp3        | 1 if the customer accepted the offer in the 3rd campaign, 0 otherwise   |
|                   | AcceptedCmp4        | 1 if the customer accepted the offer in the 4th campaign, 0 otherwise   |
|                   | AcceptedCmp5        | 1 if the customer accepted the offer in the 5th campaign, 0 otherwise   |
|                   | Response            | 1 if the customer accepted the offer in the last campaign, 0 otherwise  |
|-------------------|---------------------|----------------------------------------------------------               |
| **Place**         | NumWebPurchases     | Number of purchases made through the company’s website                  |
|                   | NumCatalogPurchases | Number of purchases made using a catalog                                |
|                   | NumStorePurchases   | Number of purchases made directly in stores                             |
|                   | NumWebVisitsMonth    | Number of visits to the company’s website in the last month            |

## 2.1 Data Overall dan Data Types <a name="sec2p1"></a>
* Semua pelanggan memiliki ID unik masing-masing (Jumlah Pelanggan = Jumlah Unik di Kolom **ID**)
Berdasarkan data diatas terdapat beberapa hal yang perlu dilakukan perapihan data dan pembersihan data pada beberapa kolom, untuk meningkatkan relevansi data dan keakuratan data yang nantinya akan dilakukan analisis, maka dibawah ini kolom yang perlu ditindak lanjuti di dalam proses *Data Cleaning* :
* Tipe data kolom **Dt_Customer** masih dalam bentuk object harus diubah menjadi datetime. Karena kolom "Dt_Customer" berisi tanggal registrasi pelanggan, maka format tipe datanya adalah tanggal waktu *(datetime)*
* Pada kolom **ID** ada 1 yang memiliki nilai 0 hal tersebut nantinya akan diubah dengan random nilai agar membantu analsis lebih relevan dan real
*  Pada kolom **Marital_Status**, didapati beberapa istilah seperti "Absurd" dan "YOLO" yang tidak relevan pengartiannya dan tidak sesuai dengan klasifikasi status perkawinan. Namun, kita dapat mengasumsikan bahwa individu yang mengisi status perkawinan ini sebenarnya masih Single karena jika mereka memiliki pasangan, mereka dapat menggunakan "Together" (akan diganti dengan "Cohabitation" [referensi](https://en.wikipedia.org/wiki/Cohabitation)) atau "Married". Selain itu, status "Single" dan "Alone" pada dasarnya memiliki arti yang sama, seperti halnya "Divorced" dan "Widow", keduanya mengindikasikan perpisahan. Untuk menyederhanakan analisis dan lebih relevan, kolom baru **"Marital_Status"** akan dibuat, yang hanya terdiri dari **"Single", "Cohabitation", "Married", dan "Divorced"** 
* Pada kolom **Education**, terdapat nilai "2n Cycle" yang menurut salah satu [sumber referensi](https://www.studera.nu/startpage/higher-education-studies/higher-education-in-sweden/study-levels-and-degrees/#:~:text=First%20cycle%20is%20for%20the,offered%20at%20all%20three%20cycles.) berarti gelar Master. Selain itu, pendidikan "Basic" mengacu pada individu yang hanya menyelesaikan pendidikan hingga sekolah menengah atas (SMA) atau memiliki pendidikan informal dan tidak melaksanakan perguruan tinggi menurut [definisi pendidikan dasar](https://uis.unesco.org/en/glossary-term/basic-education). Oleh karena itu, kami akan mengubah isi kolom 'Education', di mana "2n Cycle" akan dikelompokkan sebagai "Master", dan "Basic" akan diidentifikasi sebagai "Non-degree" menurut [referensi](https://dictionary.cambridge.org/dictionary/english/non-graduate). Selain itu, tingkat pendidikan "Graduation" akan diganti dengan "Bachelor" untuk menghindari definisi yang kurang relevan

## 2.2 Missing Values dan Duplicated Values<a name="sec2p2"></a>
![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/1692142a-de25-47ca-a33d-12175bc65db9)
**Penjelasan**
* Terdapat  nilai yang hilang `(n/a)/Null value/missing value` terdapat pada kolom `'Income' sejumlah 24 data`, hal ini akan dilakukan penanganan. **Nilai yang hilang akan ditangani di bagian selanjutnya yaitu Pembersihan Data *(Data Cleaning)***

Ada 2 cara untuk menangani *missing value*:
* **Pertama**, menghapus baris/kolom yang berisi *missing value*. Cara ini mungkin bisa dilakukan karena persentase nilai missing value yakni 1% dibawah 5% menurut sumber: [UPEI Library](https://pressbooks.library.upei.ca/montelpare/chapter/working-with-missing-data/#:~:text=Generally%2C%20if%20less%20than%205,to%20ignore%20them%20(REF)).
* **Kedua**, mengisi data yang hilang. Ada beberapa metode yang bisa digunakan untuk mengisi *missing value*, cara yang paling baik bila jumlah data missing value diatas 5% maka dengan mengisi data yang hilang dengan nilai sebenarnya, atau sedekat mungkin dengan nilai asli. Dalam kasus ini, kita akan mencoba mengisi *missing value* berdasarkan kolom lain yang secara *domain knowledge* atau secara statistik berkaitan dengan kolom yang memiliki *missing value*. Jika masih ada kolom yang tidak bisa diisi, barulah kita mengisi dengan angka *mean, median* atau *modus*. **Menghapus data akan menjadi opsi terakhir**.

Perlu dilakukan pengecekan terhadap `outlier` dalam data set yang dapat mengganggu analisis data.
# 3. **Exploratory Data Understanding (EDU)**<a name="edu"></a>
Pada bagian ini akan disajikan explorasi pemahaman data mulai dari deskriptif statistik hingga distribusi.
## 3.1 Numerik & Deskriptif <a name="edu1"></a>
Sebelum dilakukannya data cleaning, maka cek terlebih dahulu terkait distribusi data numerik

### 3.1.1 Statistik Deskriptif
![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/4db2802b-3a9b-40af-a63a-ceb51935268c)
![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/4bebcf57-6ac8-4b2a-a355-788d607d2fc1)

### 3.1.2 Distribusi Data Numerik

Ada beberapa hal terkait distribusi data numerik yang dapat kita deskripsikan dalam beberapa poin :

Ada 26 kolom data yang memiliki komposisi data yang keseluruhannya yaitu numerik
Terdapat 2240 pelanggan yang terdaftar pada data pelanggan ini yang dapat kita temukan pada count pada kolom "ID"
Pelanggan yang terdaftar juga memiliki sebaran umur yang cukup berentang, dengan umur max (paling muda) = memiliki kelahiran 1996 dan umur min (paling tua) = memiliki kelahiran 1893. Pada tahun kelahiran ini perlu kita explisit kan dan disesuaikan menjadi umur yang sesuai dengan waktu saat pendaftaran terbaru dengan menambahkan kolom baru nantinya yaitu 'Age'
Dari hasil histogram yang dapat dicermati, untuk hampir keseluruhan data numerik dapat dikategorikan data tidak normal dikarenakan hampir keseluruhan memiliki skew (buntut), selain itu data pada kolom "ID" dan "Recency" merupakan data diskrit bukan continous. Namun akan dilakukan uji statistika normalitas distribusi data agar lebih akurat dalam menentukan data normal dan tidaknya
Pada kolom Z_CostContact dan Z_Revenue memiliki distribusi data simeteris yang akan di validasi kembali pada proses korelasi (heatmap) dan boxplot untuk menentukan apakah kolom tersebut mempengaruhi proses analisis atau bisa dilakukan penghapusan kolom

### 3.1.3 Outliers

Distribusi Data Income
![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/98968358-33f5-4ed4-89dd-fc9ac69866cf)

Distribusi Data Year_Birth
![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/bcf4953d-2af8-4690-b987-7cc843d1519a)

Hasil pengecekan outliers yang didapatkan dari grafik Boxplot dan IQR ada beberapa hal yang dapat menjadi bahasan yakni :

Outliers pada masing - masing variabel/kolom yang muncul tidak serta merta akan dilakukan penghapusan
Pada variabel Income dan Year_Birth memiliki outliers yang cukup masuk akal bila dilakukan penghapusan, namun harus dilihat kembali apakah outliers tersebut bila dihapus semua akan mengurangi insight dari analisis data nantinya
Kolom untuk setiap produk memiliki jumlah pencilan kanan yang signifikan. Hal ini dikarenakan beberapa pelanggan sangat menyukai produk tertentu, sehingga mereka membelinya dalam jumlah yang jauh lebih besar daripada rata-rata orang pada umumnya.

### 3.1.4 Uji Normalitas Numerik

![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/99de1008-a0c4-4cd4-a0f1-33d6ac52f921)

Hasil yang didapat setelah dilakukan uji normalitas distribusi yakni Distribusi Data Tidak Normal dikarenakan nilai pvalue < 0.05 . Maka selanjutnya dilakukan pengecekan korelasi tiap variabel menggunakan metode .corr dan menggunakan visualisasi heatmap agar lebih jelas

### 3.1.5 Korelasi
![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/80d845b9-4dda-4b5c-8468-2e307a63bf31)

Setelah melalui 2 metode .corr dan heatmap untuk melihat seluruh korelasi antar kolomnya, didapatkan beberapa hal yang akan membantu proses analisis yakni :

* Variabel "Z_CostContact" dan "Z_Revenue" konsisten dari bentuk distribusi data histogram simetris hingga korelasi heatmap corr menunjukkan blank putih. Dapat disimpulkan bahwa 2 variabel tersebut bisa dihapus (di bagian data cleaning) karena tidak mempengaruhi data.
* Nilai korelasi yang paling baik yakni memiliki nilai yang mendekati 1 atau dengan warna yang lebih terang, bisa kita lihat dari heatmapp corr diatas beberapa contoh variabel yang memiliki korelasi baik yakni antara lain :

    1. Variabel "NumCatalogPurchases" dengan "MntMeatProudcts" dan "MntWines" dengan nilai heatmap corr 0.85 dan 0.82
    2. Variabel "Income" dengan "MntWines" dan "MntMeatProducts" dengan nilai heatmap corr 0.83 dan 0.82
    
dari variabel yang memiliki nilai korelasi yang mendekati 1 tersebut menarik untuk dilakukan analisis karena bisa jadi dari variabel tersebut terdapat insight atau temuan untuk memberikan tingkat analisis yang lebih komprehensif.

## 3.2 Kategorik<a name="edu2"></a>
![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/4078153d-1d1b-499f-8794-b3b4300c8af8)

### 3.2.1 Modus

![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/69a34a3a-f5dc-4515-9e6b-28593ec78db9)
![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/668205ae-3740-4c03-8071-c927b1d909b2)

# 4. **Data Cleaning** <a name="dclean"></a>
## 4.1 Ringkasan Data Cleaning <a name="dclean1"></a>
Dataset telah dilakukan pembersihan (Data Cleaning) dan peningkatan informasi. Adapun ringkasan (summary) sebagai berikut: 

1. Tipe data pada variabel/kolom ‘Dt_Customer’ sudah diubah menjad datetime64[ns]
2. Drop kolom (penghapusan kolom) 'Z_CostContact' dan'Z_Revenue'
3. Mengganti ID bernilai 0 dengan Random ID
4. Perbaikan komposisi data pada variabel/kolom 'Marital_Status' telah menjadi 4 kategori (Married, Cohabitation, Single dan Divorced) dan 'Education' menjadi 4 kategori (Bachelor, Master, Doctoral, Non-degree)
5. Menambahkan kolom baru guna mempermudah proses analsis (‘Age’, 'FamilyMember', 'WinesExpense' , 'FruitsExpense', 'MeatExpense', 'FishExpense', 'SweetExpense', 'GoldExpense', 'PurchasedItemTotal', 'FreqPurchased', 'PromoReceived', 'PromoAcceptedCat', 'Age_Range', 'IncomeCategory')
6. Menghapus (Drop) kolom abnormal berdasarkan temuan pada kolom  'MntWines','MntFruits','MntMeatProducts','MntFishProducts','MntSweetProducts','MntGoldProds', namun tidak pernah ada data berbelanja (checkout) pada semua data Number of Purchase
7. Menghapus Outliers pada kolom ‘Income’ dan ‘Age’
8. Melakukan inputasi missing values pada kolom ‘Income’ dengan nilai median berdasarkan ’Age_Range’,  ‘Education’, ‘Marital_Status’ yang sudah dilakukan uji normalitas pada distribusi datanya

Perubahan shape data sebelum dan sesudah :
> Before: Total Baris 2240, Total Kolom 29

> After: Total Baris 2232, Total Kolom 42
# 5. **Data Analysis** <a name="section3"></a>
## 5.1 **RFM Analysis**
![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/82263977-c3c4-49cb-8344-ae44d3ce63d2)

Analisis Hasil RFM

Hasil RFM level yang telah dilakukan dapat menjawab dari rumusan masalah sebagai berikut:
1. Bagaimana segmentasi pelanggan berdasarkan kebiasaan mereka melakukan pembelian (recency), frekuensi, dan keuangan/transaksi?

Maka jawaban yang tepat yakni pada data RFM level yang telah disajikan pada figur/pie plot. Hasil tersebut juga bisa memberikan pandangan untuk actionable solution perusahaan pada customer dengan segmentasi level ‘Promising Customer’ dan ‘Need Attention'.

Dengan memahami bagaimana pelanggan mereka tersegmentasi, perusahaan dapat mengembangkan kampanye pemasaran yang ditargetkan dan meningkatkan upaya layanan pelanggan mereka.

NOTE Hasil Segmentasi
* **Champions Customer**: Ini adalah pelanggan yang paling berharga, karena mereka baru-baru ini sering membeli dan dalam jumlah besar.
* **Loyal Customer**: Pelanggan ini telah sering membeli dan dalam jumlah yang besar, tetapi pembelian mereka tidak baru-baru ini.
* **Promising Customer**: Pelanggan ini baru saja membeli dan sering membeli, tetapi mereka belum menghabiskan banyak uang.
* **Need Attention**: Pelanggan ini baru saja membeli, tetapi tidak terlalu sering dan tidak dalam jumlah yang banyak.
* **Almost Lost Customer**: Pelanggan ini belum pernah membeli baru-baru ini.
## 5.2 **Analisis Lokasi/Saluran Pembelian Terbaik Pelanggan**
![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/87f10b9f-cfe8-43b5-9102-19dad38508a2)

Berikut adalah beberapa insight:

Para 'Promising Customers' cenderung melakukan pembelian paling banyak secara offline/direct shopping supermarket 'NumStorePurchases', diikuti oleh pembelian secara online dan katalog 'NumCatalogPurchases'. Mereka cenderung melakukan lebih sedikit pembelian melalui penawaran/diskon 'NumDealsPurchases'.
Pelanggan'Need Attention' juga sama halnya seperti 'Promising Customers', mereka termasuk proporsi dominan pelanggan kedua dari segmen pelanggan yang lain
'Loyal Customers' berada di rata-rata semua tempat dengan melakukan pembelian hampir disemua tempat dengan frekuensi yang mendekati rata-rata
'Champions' dan 'Almost Lost Customers' dan paling sedikit bila secara frekuensi pembelian namun dsitribusi lokasi/saluran transaksi yang mereka pilih lebih sedikit diseluruh tempat
Secara keseluruhan, bagan tersebut menunjukkan bahwa pembelian di dalam toko dan online adalah saluran yang paling umum di berbagai tingkat segmentasi RFM. Pembelian katalog lebih jarang terjadi, dan penawaran menggunakan diskon adalah saluran yang paling jarang terjadi.
## 5.3 **Analisis Produk Terlaris**
![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/3c5f7d64-4b4e-4cb7-87c3-4ccd1e83f56d)

Bila dilihat dari hasil grafik diatas rata-rata produk dengan pembelian terbanyak yaitu 'MntWines'/Wine dan 'MntMeatProducts'. Banyak faktor yang dapat mempengaruhi pembelian wine dan meat(daging) menjadi dominasi diantara produk-produk kebutuhan pokok yang lain. Salah satu faktor yaitu dengan melihat dari sisi segmen pelanggan. Segmen pelanggan sangat mempengaruhi produk mana yang akan diminati atau dibeli namun itu dimulai dari segmen kebiasaan yang ada pada data RFM. Selain itu dengan diketahuinya produkter laris dan jarang ini dapat membantu analisis dan rekomendasi pada tim marketing dan supplier agar memberikan solusi yang lebih spesifik pada produk yang dituju.
![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/6488a9bd-e60e-4ddb-a795-047ef1649ed8)

Grafik diatas menunjukkan bahwa segmen 'Promising Customers' membelanjakan paling banyak di semua kategori produk, diikuti oleh 'Need Attention Customers' & 'Loyal Customers'. Pelanggan 'Champions Customers' dan 'Almost Lost Customers' membelanjakan paling sedikit.

Berikut adalah perincian grafik yang lebih rinci berdasarkan kategori produk:
* MntWines: 'Promising Customers' membelanjakan paling banyak, diikuti oleh 'Need Attention Customers' dan 'Loyal Customers'.
* MntFruits: Mirip dengan MntWines, 'Promising Customers' membelanjakan paling banyak, diikuti oleh 'Need Attention Customers' dan 'Loyal Customers'.
* MntMeatProducts: 'Promising Customers' membelanjakan paling banyak, diikuti oleh 'Need Attention Customers' dan 'Loyal Customers'.
* MntFishProducts: 'Promising Customers' membelanjakan paling banyak, diikuti oleh ''Need Attention Customers' dan 'Loyal Customers'.
* MntSweetProducts: 'Promising Customers' membelanjakan paling banyak, diikuti oleh 'Loyal Customers' dan 'Promising Customers'.
* MntGoldProds: 'Promising Customers' membelanjakan paling banyak, diikuti oleh 'Need Attention Customers' dan 'Loyal Customers'.

Secara keseluruhan, poin utama yang di highlight yakni:
1. 'Need Attention' dan 'Promising Customers' adalah pembeli paling banyak di semua kategori produk. Hal ini menunjukkan bahwa mereka harus menjadi kelompok target fokus untuk kampanye pemasaran.
2. Produk MntWines dan MntMeat menjadi produk yang lebih banyak dibeli dari produk-produk yang lain. Ini dapat menjadi bahan pengembangan serta evaluasi untuk perusahaan agar lebih melakukan maintain produk dan mengembangkan marketing atau promosi lebih spesifik.

## 5.4 **Analisis Efektifitas Promosi**
![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/310fb6f1-3459-4390-8615-ed7f2ce01417)
![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/6172b75d-62db-402c-9913-297dc2415544)
![image](https://github.com/awsyahnanda/supermarket-sales-project/assets/158844436/be96788f-7a82-45d7-9861-eb2c3c6e29db)

Berikut adalah beberapa pengamatan pada grafik diatas:

* Dalam segi pelanggan yang menerima promo/campaign bahwasanya campaign terakhir yang memiliki penerimaan promo dari saluran/transaksi diskon yang cukup banyak dari campaign yang lain. Hal ini banyak faktor yang mempengaruhi, salah satunya yaitu segmentasi pelanggan. Maka hal ini bisa jadi evaluasi bagi tim marketing untuk melakukan segmentasi promosi terukur mengarah ke segmen pelanggan tertentu
* Champions dan Loyal Customers tampaknya merupakan segmen yang paling menonjol. Mereka adalah pelanggan bernilai tinggi yang cenderung sering melakukan pembelian dan baru-baru ini. Mereka mungkin juga merupakan pelanggan yang paling banyak membelanjakan uangnya.
* Almost Lost Customers dan Need Attention tampak lebih kecil daripada segmen Pelanggan Juara dan Pelanggan Setia. Mereka mungkin adalah pelanggan yang belum pernah membeli baru-baru ini atau belum menghabiskan banyak uang.
* Jumlah Promising Customers sangat sedikit. Mereka bisa jadi adalah pelanggan baru yang baru melakukan sedikit pembelian namun memiliki potensi untuk menjadi pelanggan yang lebih berharga di masa depan.

Maka dari analisa tersebut hadil pada efektifitas promosi yakni **kurang efektif** berdasarkan penerimaan campaign/promosi dari keseluruhan member hanya sebesar 27.2% dan didukung data penggunaan diskon pada transaksi hanya dominan pada campaign terakhir. Maka diperlukannya evaluasi dan pengembangan strategi promosi yang lebih baik. Contohnya mengarah ke segmentasi pelanggan yang 'Loyal','Champions' & 'Promising Customers' untuk memberikan campaign tertentu.

# 6. **Kesimpulan dan Rekomendasi** <a name="section4"></a>
## 6.1 **Kesimpulan**
**1.  Berikut adalah beberapa kesimpulan dari segmentasi pelanggan melalui RFM:**

* Pelanggan dengan segmen 'Need Attention' dan 'Promising Customers' mendominasi jumlah pelanggan member supermarket dengan total masing-masing 45.4% dan 34.7% dari 2332 pelanggan member.
* Penargetan pelanggan yang lebih baik dengan melakukan segmentasi pelanggan, dapat menargetkan kampanye pemasaran kepada orang yang tepat seperti pelanggan 'Need Attention' dan 'Promising Customers'. Hal ini dapat membantu  meningkatkan laba atas investasi (ROI).
* Peningkatan kepuasan pelayanan ke pelanggan dengan memahami kebutuhan segmen pelanggan yang berbeda, dapat disesuaikan produk dan layanan perusahaan untuk memenuhi kebutuhan tersebut dengan lebih baik. Hal ini dapat meningkatkan kepuasan pelanggan.

**2. Berikut beberapa kesimpulan dari lokasi/saluran transaksi pelanggan:**

* Secara keseluruhan hasil analisa lokasi/saluran transaksi pelanggan, kesimpulan menunjukkan bahwa **'WebPurchases' dan 'StorePurchases 'adalah saluran yang paling umum di berbagai tingkat segmentasi RFM**. Pembelian 'CatalogPurchases' lebih jarang terjadi, dan 'NumDealsPurchases/penawaran menggunakan diskon' adalah saluran yang paling jarang terjadi.
* Dengan memahami bagaimana lokasi/saluran transaksi pelanggan bervariasi tergantung pada tingkat RFM, supermarket dapat mengembangkan campaign pemasaran yang ditargetkan untuk menjangkau segmen pelanggan yang berbeda melalui saluran pilihan mereka. Misalnya, supermarket dapat menargetkan 'Promising Customers' dengan promosi yang mendorong mereka untuk berbelanja online, atau mereka dapat menargetkan Pelanggan 'Need Attention' dengan penawaran online eksklusif.

**3. Berikut beberapa kesimpulan dari analisa produk terlaris di supermarket:**

* Produk MntWines dan MntMeat menjadi produk yang lebih banyak dibeli dari produk-produk yang lain dengan total proporsi 77.8%. Ini dapat menjadi bahan pengembangan serta evaluasi untuk perusahaan agar lebih melakukan maintain produk dan mengembangkan marketing atau promosi lebih spesifik.
* Produk kebutuhan pokok yang lain mungkin perlu dilakukan evalusi lebih lanjut dalam segi kualitas dan harga, namun hal ini perlu dibutuhkan data tambahan untuk membantu proses analisa sesuai kebutuhan.

**4. Berikut beberapa kesimpulan dari analisa efektifitas campaign/promosi dari supermarket:**

* Dengan memahami kebutuhan segmen pelanggan yang berbeda, dapat mengembangkan strategi untuk mempertahankan mereka(pelanggan) lebih lama. Hal ini dapat membantu meningkatkan lifetime value hidup pelanggan.
* Efektifitas promosi yakni **kurang efektif** berdasarkan penerimaan campaign/promosi dari keseluruhan member hanya sebesar 27.2% dan didukung data penggunaan diskon pada transaksi hanya dominan pada campaign terakhir. Maka diperlukannya evaluasi dan pengembangan strategi promosi yang lebih baik. Contohnya mengarah ke segmentasi pelanggan yang 'Loyal','Champions' & 'Promising Customers' untuk memberikan campaign tertentu.
## 6.2 **Rekomendasi**

**Rekomendasi:**
1. **Fokus Pelanggan Tersegmentasi:**
    - Mengkonsentrasikan upaya pada segmen pelanggan yang lebih besar, khususnya 'Need Attention' dan 'Promising Customers', yang bersama-sama mencakup lebih dari 80% dari total pelanggan. Kembangkan strategi pemasaran untuk melibatkan dan mempertahankan serta meningkatkan segmen ini. [Referensi](https://www.researchgate.net/publication/300791265_Retail_Store_Segmentation_for_Target_Marketing)
2. **Mitigasi Risiko dan Program Loyalitas/Poin Supermarket:**
    - Menerapkan upaya yang ditargetkan untuk kategori 'Need Attention', yang mencakup 45,4% pelanggan, untuk mencegah potensi masalah atau pelepasan. Merancang program loyalitas/Poin Redeem atau promosi khusus untuk segmen 'Champions Customers' yang lebih kecil namun bernilai (2,5%).
3. **Alokasi Sumber Daya Strategis:**
    - Mengakui ketidakseimbangan distribusi dan mengalokasikan sumber daya secara strategis. Mengatasi kebutuhan segmen yang lebih besar dapat menghasilkan perbaikan yang lebih besar secara keseluruhan.
4. **Inisiatif yang Disesuaikan:**
    - Menyesuaikan inisiatif berdasarkan karakteristik spesifik setiap segmen. Terapkan intervensi yang lebih intensif untuk kategori 'Need Attention' dan pertimbangkan program pengakuan atau loyalitas untuk segmen 'Loyal Customers'.
5. **Strategi Produk:**
    - Fokuskan upaya pemasaran pada kategori produk dengan pembelanjaan tinggi seperti Wine dan Produk Meat (Daging). Sesuaikan inventaris dan strategi promosi berdasarkan pola belanja pelanggan.
6. **Segmentasi Pelanggan untuk Pemasaran:**
    - Menyesuaikan strategi pemasaran untuk menargetkan 'Potensi Loyalis' untuk diakuisisi, sekaligus mempertahankan dan meningkatkan penjualan ke segmen 'Loyal Customers'.
7. **Strategi Retensi:**
    - Mengembangkan strategi retensi yang ditargetkan untuk pelanggan 'Need Attention' untuk mencegah potensi churn. Terapkan kampanye keterlibatan kembali untuk memahami dan memenuhi kebutuhan mereka.
8. **Pengoptimalan Kampanye:**
    - Menganalisis keberhasilan kampanye pemasaran, dengan fokus mengubah pelanggan 'Loyal Customers' dan 'Need Attention' menjadi pelanggan setia. Pertimbangkan untuk menyesuaikan kampanye agar lebih sesuai dengan preferensi pelanggan 'Loyal Customers'.
    - Dapat menargetkan pelanggan yang 'Need Attention' dengan kampanye [win-back](https://www.campaignmonitor.com/resources/knowledge-base/what-is-a-win-back-campaign/), sementara bisnis tersebut dapat menargetkan 'Loyal Customers' dengan program loyalitas.
9. **Pendekatan Multisaluran:**
    - Memperkuat platform online untuk meningkatkan kenyamanan pembelian melalui web. Kembangkan pengalaman yang dipersonalisasi untuk pembelian di dalam toko dan katalog untuk memenuhi beragam preferensi pelanggan.
    - Memberikan pelayanan secara kekeluargaan pada saat pelanggan berada pada lokasi supermarket agar meningkatkan kenyamanan serta pengalaman berada di supermarket
10. **Peningkatan Berkelanjutan:**
    - Secara teratur menilai kembali data pelanggan, umpan balik, dan tren pasar untuk menyesuaikan strategi. Perbaikan berkelanjutan sangat penting untuk memenuhi kebutuhan pelanggan yang terus berkembang dan dinamika pasar.

Rekomendasi ini bertujuan untuk memandu pengambilan keputusan strategis, meningkatkan kepuasan pelanggan, dan meningkatkan hasil bisnis secara keseluruhan berdasarkan wawasan berbeda yang diperoleh dari data yang diberikan.

## 7. Referensi <a name="section5"></a>

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

- [10] Supermarket Customer Dataset
https://drive.google.com/drive/folders/1WodnBbuYTvsF0-6HTuQABQ0KCS31lqbK?usp=sharing

- [11] IPython
https://ipython.org/

- [12] statsmodels: Statistics in Python
https://www.statsmodels.org/stable/index.html

- [13] scipy.stats : Statistics with SciPy
https://docs.scipy.org/doc/scipy/reference/tutorial/stats.html
