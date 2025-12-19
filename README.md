# 📘 Judul Proyek
*Klasifikasi Tingkat Kelangsungan Hidup Pasien Penyakit Hepatitis Menggunakan Algoritma Machine Learning Berbasis Data Klinis*

## 👤 Informasi
- **Nama:** [Chandra Dina Sefrilian]  
- **Repo:** [https://github.com/ChandraDina/Hepatits-DataSet-Projek.git]  
- **Video:**[https://drive.google.com/file/d/1JITM-ebSj8owbsMR4bu009SHrMg_AoQy/view?usp=drive_link]  

---

# 1. 🎯 Ringkasan Proyek
- Menyelesaikan permasalahan sesuai domain  
- Melakukan data preparation  
- Membangun 3 model:
  **Nave Bayes**
  Pada model Gaussian Naive Bayes, tidak banyak hyperparameter yang perlu diatur karena model ini bersifat sederhana. Dalam implementasi ini, model dijalankan menggunakan pengaturan default, di mana parameter utama yang digunakan adalah var_smoothing. Parameter ini berfungsi untuk menambahkan nilai kecil pada varians data guna mencegah pembagian dengan nol dan menjaga kestabilan perhitungan probabilitas. Dengan menggunakan nilai default, model dapat langsung dilatih tanpa proses tuning yang kompleks, sehingga cocok digunakan sebagai model baseline untuk pembanding.
  **Random Forest**
  Random Forest merupakan model klasifikasi yang bekerja dengan menggabungkan banyak pohon keputusan untuk menghasilkan prediksi yang lebih stabil dan akurat. Setiap pohon dilatih menggunakan bagian data yang berbeda, kemudian hasil prediksinya digabungkan melalui proses voting. Pada model ini digunakan 100 pohon keputusan untuk mempelajari pola data pasien hepatitis. Model dilatih menggunakan data latih dan dievaluasi pada data uji untuk mengetahui tingkat akurasinya dalam memprediksi status pasien.
  **Super Vector Machine**
  Model kedua yang digunakan adalah Support Vector Machine (SVM) dengan kernel Radial Basis Function (RBF). Model ini bekerja dengan mencari garis pemisah (hyperplane) terbaik yang mampu memisahkan data ke dalam dua kelas dengan margin maksimal. Penggunaan kernel RBF memungkinkan model untuk menangkap pola data yang bersifat non-linear, sehingga lebih fleksibel dalam memisahkan data pasien hepatitis yang memiliki karakteristik kompleks. Model dilatih menggunakan data latih dan kemudian digunakan untuk memprediksi kelas pada data uji. Performa model dievaluasi menggunakan nilai akurasi untuk mengetahui kemampuan SVM dalam mengklasifikasikan status pasien.
  
- Melakukan evaluasi dan menentukan model terbaik
Setiap model dievaluasi menggunakan metrik yang relevan untuk data kesehatan, di mana kesalahan prediksi pada kelas minoritas (pasien         meninggal) memiliki risiko yang jauh lebih tinggi.

---

# 2. 📄 Problem & Goals
**Problem Statements:**  
- [1. Bagaimana mengidentifikasi secara akurat apakah seorang pasien hepatitis memiliki kemungkinan untuk bertahan hidup atau meninggal dunia berdasarkan indikator klinis yang tersedia.]  
- [2. Terdapat tantangan berupa data medis yang tidak lengkap (missing values) dan jumlah sampel yang terbatas dalam melakukan diagnosis manual]  

**Goals:**  
- [1. Mengembangkan model klasifikasi otomatis yang mampu memprediksi status kelangsungan hidup pasien dengan tingkat akurasi yang tinggi.]  
- [2.Menganalisis perbandingan performa antara berbagai algoritma untuk menemukan solusi komputasi terbaik bagi tenaga medis ]  

---
## 📁 Struktur Folder
```
project/
│
├── data/                   # Dataset (tidak di-commit, download manual)
│
├── notebooks/              # Jupyter notebooks
│   └── ML_Project.ipynb
│
├── src/                    # Source code
│   
├── models/                 # Saved models
│   ├── svm_model.pkl
│   ├── Random_Forest_.pkl
│   └── Deep_learning.h5
|   |__ Naive_bayes_model.pkl
│
├── images/                 # Visualizations
│   └── r
│
├── requirements.txt        # Dependencies
├── .gitignore
└── README.md
```
---

# 3. 📊 Dataset
- **Sumber:** [UCI Machine Learning Repository (Hepatitis Dataset)]  
- **Jumlah Data:** [155 sampel pasien (data relatif terbatas)] 
- **Tipe:** [Multivariate (Kombinasi fitur kategorikal, boolean, dan numerik).]  

### Fitur Utama
| Fitur | Deskripsi |
| Age   | Rentang usia pasien|
| Sex   | Jenis kelamin
|Billirubin, Albumin, SGOT | Hasil pemeriksaan laboratorium biokimia |
| Ascites | Gejala klinis fisik yang teramati pada pasien |
| Class (target) | Status akhir pasien : Hidup atau meninggal |

---

# 4. 🔧 Data Preparation
- Cleaning (missing/duplicate/outliers)
  Menangani nilai kosong ("?") dengan teknik imputasi: rata-rata (mean) untuk data numerik dan nilai tersering (mode) untuk data kategori
- Transformasi (encoding/scaling)
   Mengonversi data kategori menjadi format biner (encoding) dan melakukan standarisasi fitur numerik menggunakan StandardScaler agar bobot model seimbang.
- Splitting (train/val/test)
  Membagi dataset secara objektif dengan rasio 80% untuk pelatihan (training) dan 20% untuk pengujian (testing)

---

# 5. 🤖 Modeling
- **Model 1 – Gaussian Naive Bayes:** [Menggunakan pendekatan probabilistik sederhana dengan asumsi independensi antar fitur untuk memberikan standar performa awal]  
- **Model 2 – Support Vector Machine:** [Menggunakan kernel Radial Basis Function (RBF) untuk menangkap pola data yang bersifat non-linear agar pemisahan kelas lebih optimal.]  
- **Model 3 – random Forest:** [Terdiri dari 100 pohon keputusan (decision trees) yang bekerja secara kolektif untuk meminimalkan kesalahan prediksi dan meningkatkan stabilitas model]  

---

# 6. 🧪 Evaluation
**Metrik:** 
 Akurasi (Accuracy) digunakan untuk mengukur sejauh mana model mampu mengklasifikasikan data uji dengan tepat.
### Hasil Singkat
| Model | Score | Catatan |
|------|--------|---------|
| Naive Bayes | [67,7%] |Cukup untuk baseline, namun terbatas oleh asumsi independensi  |
| SVM| [74,1%] |Lebih baik dalam menangani pola data klinis yang kompleks. |
| Random Forest| [74,1%] |Memberikan hasil paling stabil melalui mekanisme voting mayoritas |

---

# 7. 🏁 Kesimpulan
- Model terbaik: [Random Forest]  
- Alasan: [Meskipun memiliki akurasi yang sama dengan SVM pada pengujian ini, Random Forest dinilai paling stabil karena mampu mereduksi risiko overfitting dan lebih efektif menangani variasi fitur pada dataset hepatitis]  
- Insight penting: [Proses preprocessing data (seperti penanganan missing values dan SMOTE) sangat krusial dalam menentukan keberhasilan model pada dataset medis yang terbatas]  

---

# 8. 🔮 Future Work
- [ ] Mengumpulkan dataset tambahan atau menggunakan data dari institusi kesehatan lain untuk meningkatkan generalisasi model. 
- [ ] Melakukan hyperparameter tuning yang lebih mendalam pada model SVM dan Random Forest.
- [ ] Mencoba arsitektur Deep Learning (ANN) untuk melihat potensi peningkatan performa pada data besar.


---

# 9. 🔁 Reproducibility
Gunakan environment:
Language : Python
Libraries : NumPy, Pandas, Scikit-learn, TensorFlow
