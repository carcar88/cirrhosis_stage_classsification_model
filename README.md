# Cirrhosis Stage Classsification Model
**Tujuan:**  
Membangun model klasifikasi _stage_ cirrhosis pasien berdasarkan hasi tes pasien.  
**Metodologi:**  
Projek ini menghasilkan dua model dengan metodologi yang berbeda, yaitu _random forest_ dan XGBoost. Kedua model ini dipilih karena kemampuannya untuk menganalisa dan menangkap hubungan rumit antara variabel yang dimiliki.   

**Fitur-fitur _Dataset_:**  
| _Parameter_ | _Description_ | _Unit_ |
| :--- | :--- | :--- |
| ID | The individual’s patient ID | - |
| Registration Date | The individual’s registration date at the hospital | - |
| Drug | Type of drug given to the individual (D-penicillamine or placebo) | - |
| Birth Date | The birth date of the individual | - |
| Gender | The gender of the individual | - |
| Ascites | Presence of ascites | (Y/N) |
| Hepatomegaly | Presence of hepatomegaly | (Y/N) |
| Edema | Presence of edema | (N=no edema, S=edema without diuretics, Y=edema despite diuretic therapy) |
| Bilirubin | Serum bilirubin | mg/dL |
| Cholesterol | Serum cholesterol | mg/dL |
| Albumin | Amount of albumin | g/dL |
| Copper | Amount of copper found in urine | μg/day |
| Alkaline Phospatase | Alkaline phosphatase | U/L |
| SGOT | Serum Glutamic-Oxaloacetic Transaminase | U/mL |
| Triglycerides | Amount of triglycerides | mg/dL |
| Platelets | Platelets per cubic | mL/1000 |
| Prothrombin | Prothrombin time | s |
| Stage | Histologic stage of the cirrhosis | - |


**Proses Analisis dan Pemodelan:**  
1.	_Exploratory Data Analysis_ (EDA)  
EDA dilakukan lewat pengecekan data type tiap kolum dan deteksi kesalahan _input_ pada setiap kolum.   
2.	Pembersihan dan _preprocessing_ data  
Pada tahap ini, dilakukan perbaikan _input_ yang dideteksi di tahap sebelumnya seperti _typo_. Selain itu, dilakukan standardisasi penulisan kategori. Selanjutnya, dilakukan deteksi dan penanganan _missing value_ dan _outlier_. Imputasi _missing value_ dilakukan berdasarkan _stage_ cirrhosis pada data tersebut. Data kategoris kemudian di-_encode_. Terakhir, kolum ‘Registrattion Date’ dan ‘Birth Date’ digunakan untuk membuat variabel ‘Age’.  
3.	Pemodelan  
Sebelum melakukan pemodelan, _dataset_ yang dimiliki dibagi menjadi _training_ dan _testing_ _dataset_ dengan rasio train:test 80%:20%. Sebelum membangun model _random forest_, dilakukan _grid search_ untuk menentukan _hyperparameter_ terbaik. Setelah _hyperparameter_ terbaik ditemukan, _random forest model_ dibangun dan dilatih kembali. _Grid search_ juga dilakukan pada model kedua, yaitu _XGBoost model_. Kemudian, model dilatih kembali menggunakan _hyperparameter_ terbaik.   
4.	Evaluasi  
Evaluasi dilakukan dengan bantuan _function_ classification_report milik scikit-learn. Skor yang diukur adalah _precision_, _recall_, dan _f1-score_. Evaluasi dilakukan terhadap kedua model yang dibuat.

**Hasil dan Kesimpulan:**  
Kedua model dapat memprediksi _stage_ cirrhosis pasien dengan baik, namun akurasinya masih bisa ditingkatkan lagi. Berdasarkan hasil evaluasi, model XGBoost memiliki akurasi yang lebih tinggi daripada model _random forest_. Berdasarkan model XGBoost, fitur yang paling berpengaruh terhadap _stage_ cirrhosis pasien adalah ‘Cholesterol’. Berikut adalah hasil evaluasi kedua model:  
_Weighted average_ dari _random forest_:   
_Precision_: 0.85    
_Recall_: 0.83    
_F1_: 0.83   

_Weighted average_ dari XGBoost:   
_Precision_: 0.87   
_Recall_: 0.87   
_F1_: 0.87   
 
**_Library_ yang Digunakan:**  
•	numpy  
•	pandas  
•	matplotlib.pyploy  
•	scikit-learn  
