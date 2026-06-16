# Machine-Learning-Terapan 🙌

## 📌 Project Prediksi Diabetes Menggunakan Random Forest

# Prediksi Risiko Diabetes Menggunakan Algoritma Random Forest

## 👥 Anggota Kelompok

1. Aldiana Putra  (233051101)
2. Muhammad Farhan Maulana Ardiansyah (2330511038)

---

# Business Understanding

## Latar Belakang

Diabetes merupakan salah satu penyakit kronis yang banyak dialami masyarakat di seluruh dunia. Penyakit ini terjadi ketika kadar gula dalam darah berada pada tingkat yang tinggi akibat gangguan produksi atau penggunaan insulin oleh tubuh. Jika tidak terdeteksi sejak dini, diabetes dapat menyebabkan berbagai komplikasi serius seperti penyakit jantung, gangguan ginjal, kerusakan saraf, hingga kebutaan.

Perkembangan teknologi Machine Learning memungkinkan proses identifikasi risiko diabetes dilakukan secara otomatis berdasarkan data kesehatan pasien. Dengan memanfaatkan data historis pasien, model Machine Learning dapat membantu tenaga kesehatan dalam melakukan deteksi dini terhadap kemungkinan seseorang menderita diabetes.

Oleh karena itu, pada proyek ini dilakukan pembangunan model prediksi diabetes menggunakan algoritma Random Forest untuk membantu mengidentifikasi risiko diabetes berdasarkan beberapa parameter kesehatan.

## Problem Statement

1. Bagaimana membangun model Machine Learning yang dapat memprediksi risiko diabetes?
2. Faktor kesehatan apa yang paling berpengaruh terhadap risiko diabetes?
3. Seberapa baik performa algoritma Random Forest dalam melakukan klasifikasi diabetes?

## Goals

1. Menghasilkan model klasifikasi diabetes menggunakan algoritma Random Forest.
2. Mengidentifikasi faktor-faktor yang memengaruhi risiko diabetes.
3. Mengevaluasi performa model menggunakan berbagai metrik evaluasi.

## Solution Statement

Solusi yang digunakan dalam proyek ini adalah menerapkan algoritma Random Forest Classifier karena memiliki kemampuan yang baik dalam menangani data klasifikasi dan mampu mengurangi risiko overfitting.

---

# Data Understanding

## Informasi Dataset

Dataset yang digunakan adalah **Pima Indians Diabetes Dataset**.

Dataset berisi data kesehatan pasien wanita keturunan Pima Indian yang digunakan untuk memprediksi kemungkinan menderita diabetes.

### Jumlah Data

- Total Data: 768
- Jumlah Fitur: 8
- Jumlah Target: 1

### Target

- 0 = Tidak Diabetes
- 1 = Diabetes

## Deskripsi Variabel

| Variabel | Keterangan |
|-----------|------------|
| Pregnancies | Jumlah kehamilan |
| Glucose | Kadar glukosa darah |
| BloodPressure | Tekanan darah |
| SkinThickness | Ketebalan lipatan kulit |
| Insulin | Kadar insulin |
| BMI | Body Mass Index |
| DiabetesPedigreeFunction | Riwayat keturunan diabetes |
| Age | Umur |
| Outcome | Status diabetes |

## Exploratory Data Analysis (EDA)

Analisis awal dilakukan untuk memahami karakteristik dataset.

Tahapan yang dilakukan:

- Melihat jumlah data
- Memeriksa tipe data
- Memeriksa missing value
- Memeriksa data duplikat
- Analisis distribusi target
- Analisis korelasi antar fitur

Berdasarkan hasil analisis, fitur Glucose, BMI, dan Age memiliki pengaruh yang cukup besar terhadap status diabetes.

---

# Data Preparation

Tahap Data Preparation dilakukan untuk menyiapkan data sebelum proses pelatihan model.

## Pemeriksaan Missing Value

Dilakukan pengecekan nilai kosong menggunakan:

```python
df.isnull().sum()
```

Hasil menunjukkan tidak terdapat missing value pada dataset.

## Pemeriksaan Data Duplikat

Dilakukan pengecekan menggunakan:

```python
df.duplicated().sum()
```

## Pemisahan Fitur dan Target

```python
X = df.drop('Outcome', axis=1)
y = df['Outcome']
```

## Train Test Split

Dataset dibagi menjadi:

- 80% Data Training
- 20% Data Testing

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

---

# Modeling

## Algoritma Random Forest

Random Forest merupakan algoritma ensemble learning yang bekerja dengan membangun banyak pohon keputusan (Decision Tree) dan menggabungkan hasil prediksinya.

### Keunggulan Random Forest

- Memiliki akurasi tinggi
- Mengurangi risiko overfitting
- Dapat menangani data kompleks
- Menyediakan fitur importance

### Parameter Model

```python
from sklearn.ensemble import RandomForestClassifier

rf_model = RandomForestClassifier(
    n_estimators=100,
    random_state=42
)
```

### Training Model

```python
rf_model.fit(X_train, y_train)
```

### Prediksi

```python
y_pred = rf_model.predict(X_test)
```

---

# Evaluation

Evaluasi dilakukan menggunakan beberapa metrik:

- Accuracy
- Precision
- Recall
- F1-Score
- Confusion Matrix

## Accuracy

```python
from sklearn.metrics import accuracy_score

accuracy = accuracy_score(y_test, y_pred)

print("Accuracy:", accuracy)
```

## Classification Report

```python
from sklearn.metrics import classification_report

print(classification_report(y_test, y_pred))
```

## Confusion Matrix

```python
from sklearn.metrics import confusion_matrix

cm = confusion_matrix(y_test, y_pred)
print(cm)
```

## Hasil Evaluasi

Contoh hasil evaluasi:

| Metrik | Nilai |
|---------|--------|
| Accuracy | 78.57% |
| Precision | 77% |
| Recall | 74% |
| F1-Score | 75% |

Hasil menunjukkan bahwa model mampu melakukan klasifikasi diabetes dengan performa yang cukup baik.

---

# Feature Importance

Random Forest dapat menunjukkan fitur mana yang paling berpengaruh terhadap prediksi.

```python
importance = pd.DataFrame({
    'Feature': X.columns,
    'Importance': rf_model.feature_importances_
})

importance.sort_values(
    by='Importance',
    ascending=False
)
```

### Fitur Terpenting

1. Glucose
2. BMI
3. Age
4. DiabetesPedigreeFunction

Dari hasil tersebut dapat diketahui bahwa kadar glukosa memiliki pengaruh terbesar terhadap risiko diabetes.

---

# Deployment

## Tujuan Deployment

Deployment dilakukan agar model dapat digunakan secara langsung oleh pengguna melalui antarmuka web.

## Teknologi yang Digunakan

- Python
- Scikit-Learn
- Gradio

## Cara Menjalankan

Install seluruh library:

```bash
pip install -r requirements.txt
```

Jalankan aplikasi:

```bash
python app.py
```

Kemudian aplikasi akan berjalan pada browser dan siap digunakan untuk melakukan prediksi.

---

# Kesimpulan

Berdasarkan hasil penelitian yang telah dilakukan, algoritma Random Forest berhasil digunakan untuk membangun model prediksi risiko diabetes dengan tingkat akurasi yang cukup baik. Model mampu memanfaatkan berbagai parameter kesehatan seperti kadar glukosa, BMI, tekanan darah, dan usia untuk menentukan kemungkinan seseorang menderita diabetes.

Hasil evaluasi menunjukkan bahwa Random Forest memiliki performa yang baik dalam melakukan klasifikasi. Selain itu, implementasi model menggunakan Gradio memungkinkan pengguna melakukan prediksi secara mudah melalui antarmuka web sederhana.

Dengan demikian, sistem yang dibangun dapat digunakan sebagai alat bantu dalam mendukung deteksi dini risiko diabetes sehingga dapat membantu proses pengambilan keputusan yang lebih cepat dan tepat.

---

# Referensi

1. Breiman, L. (2001). Random Forests. Machine Learning.
2. Dua, D., & Graff, C. (2019). UCI Machine Learning Repository.
3. Géron, A. (2022). Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow.
4. Han, J., Kamber, M., & Pei, J. Data Mining: Concepts and Techniques.
