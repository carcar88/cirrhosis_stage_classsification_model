# Cirrhosis Stage Classsification Model
**Tujuan:**  
Membangun model klasifikasi tahapan cirrhosis pasien berdasarkan hasi tes pasien.  
**Metodologi:**  
Projek ini menghasilkan dua model dengan metodologi yang berbeda, yaitu random forest dan XGBoost. Kedua model ini dipilih karena kemampuannya untuk menganalisa dan menangkap hubungan rumit antara variabel yang dimiliki.   

**Fitur-fitur Dataset:**  
| Parameter | Description | Unit |
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
1.	Exploratory Data Analysis (EDA)  
EDA dilakukan lewat pengecekan data type tiap kolum dan deteksi kesalahan input pada setiap kolum.   
2.	Pembersihan dan preprocessing data  
Pada tahap ini, dilakukan perbaikan input yang dideteksi di tahap sebelumnya seperti typo. Selain itu, penulisan kategori distandardisasi. Selanjutnya, dilakukan deteksi dan penanganan missing value dan outlier. Imputasi missing value dilakukan berdasarkan stage cirrhosis pada data tersebut. Data kategoris kemudian di-encode. Terakhir, kolum ‘Registrattion Date’ dan ‘Birth Date’ digunakan untuk membuat variabel ‘Age’.  
3.	Pemodelan  
Sebelum melakukan pemodelan, dataset yang dimiliki dibagi menjadi training dan testing dataset dengan rasio train:test 80%:20%. Sebelum membangun model random forest, dilakukan grid search untuk menentukan hyperparameter terbaik. Setelah hyperparameter terbaik ditemukan, random forest model dibangun dan dilatih kembali. Grid search juga dilakukan pada model kedua, yaitu XGBoost model. Kemudian, model dilatih kembali menggunakan hyperparameter terbaik.   
4.	Evaluasi  
Evaluasi dilakukan dengan bantuan function classification_report milik scikit-learn. Skor yang diukur adalah precision, recall, dan f1-score. Evaluasi dilakukan terhadap kedua model yang dibuat.

**Hasil dan Kesimpulan:**  
Kedua model dapat memprediksi stage cirrhosis pasien dengan baik, namun akurasinya masih bisa ditingkatkan lagi. Berdasarkan hasil evaluasi, model XGBoost memiliki akurasi yang lebih tinggi daripada model random forest. Berdasarkan model XGBoost, fitur yang paling berpengaruh terhadap stage cirrhosis pasien adalah ‘Cholesterol’. Berikut adalah hasil evaluasi kedua model:  
Weighted average dari random forest:   
Precision: 0.85    
Recall: 0.83    
F1: 0.83   

Weighted average dari XG Boosting:   
Precision: 0.87   
Recall: 0.87   
F1: 0.87   
 
Library yang digunakan:  
•	numpy  
•	pandas  
•	matplotlib.pyploy  
•	scikit-learn  
