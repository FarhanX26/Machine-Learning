# Machine-Learning-Terapan 🙌

## 📌 Project Prediksi Diabetes Menggunakan Random Forest

### 📖 Deskripsi
Proyek ini bertujuan untuk memprediksi risiko diabetes menggunakan algoritma Machine Learning Random Forest berdasarkan data kesehatan pasien dari Pima Indians Diabetes Dataset.

### 📂 Repository Structure

```bash
.
├── diabetes_prediction.ipynb
├── diabetes.csv
├── model.pkl
├── app.py
├── requirements.txt
└── README.md
```

### 🔗 Link Project

- 📓 **Notebook / Code**
  - [Google Colab](https://colab.research.google.com/)
  - [Jupyter Notebook](./diabetes_prediction.ipynb)

- 📄 **Laporan**
  - [README Project](./README.md)

- 🚀 **Deployment**
  - [Gradio App](#)

---

## 📊 Dataset

Dataset yang digunakan adalah **Pima Indians Diabetes Dataset**.

Fitur yang digunakan:

- Pregnancies
- Glucose
- BloodPressure
- SkinThickness
- Insulin
- BMI
- DiabetesPedigreeFunction
- Age

Target:

- 0 = Tidak Diabetes
- 1 = Diabetes

---

## ⚙️ Algoritma

Model yang digunakan:

- Random Forest Classifier

Parameter:

```python
RandomForestClassifier(
    n_estimators=100,
    random_state=42
)
```

---

## 📈 Evaluation

Metode evaluasi:

- Accuracy
- Precision
- Recall
- F1-Score
- Confusion Matrix

---

## 🛠️ Deployment

Deployment dibuat menggunakan:

- Gradio
- Python
- Scikit-Learn

Jalankan:

```bash
pip install -r requirements.txt
python app.py
```

---

## 👨‍💻 Anggota Kelompok

1. Nama Anda
2. Nama Teman Kelompok

---

## 🎯 Hasil

Model berhasil melakukan prediksi risiko diabetes berdasarkan data kesehatan pasien dan dapat digunakan melalui antarmuka web sederhana menggunakan Gradio.
