# 📊 Praktikum 3 PEMSIN: Decision Tree & Linear Regression

**Raihan Daris** · NIM 202431033

Kumpulan notebook praktikum Machine Learning menggunakan **Python** dan **scikit-learn**. Repositori ini berisi dua studi kasus:

1. **Decision Tree** untuk klasifikasi jenis bunga Iris.
2. **Linear Regression** untuk memprediksi nilai numerik, mulai dari kasus sederhana (tinggi vs berat badan) sampai dataset yang lebih besar (probabilitas kebotakan).

---

## 📁 Struktur Repositori

```
.
├── Decision Tree.ipynb      # Klasifikasi bunga Iris dengan Decision Tree
├── Linear_Regression.ipynb  # Regresi linear sederhana & berganda
├── iris-flower.csv          # Dataset Iris (150 baris)
├── botak.csv                # Dataset probabilitas kebotakan (7.991 baris)
└── README.md
```

---

## 🌸 1. Decision Tree: Klasifikasi Bunga Iris

**Notebook:** [`Decision Tree.ipynb`](Decision%20Tree.ipynb)
**Dataset:** [`iris-flower.csv`](iris-flower.csv)

### Dataset
150 sampel bunga Iris, masing-masing 50 sampel untuk 3 spesies, tanpa *missing value*.

| Kolom | Keterangan |
|---|---|
| `SepalLengthCm` | Panjang sepal (cm) |
| `SepalWidthCm` | Lebar sepal (cm) |
| `PetalLengthCm` | Panjang petal (cm) |
| `PetalWidthCm` | Lebar petal (cm) |
| `Species` | Target: `Iris-setosa`, `Iris-versicolor`, `Iris-virginica` |

### Alur Kerja
1. **Pre-processing**: kolom `Species` di-encode dengan `LabelEncoder` (0 = setosa, 1 = versicolor, 2 = virginica), kolom `Id` dibuang dari fitur.
2. **Split data**: 75% data latih, 25% data uji (`random_state=0`).
3. **Modelling**: `DecisionTreeClassifier` dengan parameter default, lalu dibandingkan dengan `criterion='entropy'` dan `max_depth=5`.
4. **Visualisasi**: pohon keputusan digambar dengan `sklearn.tree.plot_tree`.
5. **Evaluasi & prediksi**: akurasi pada data uji dan contoh prediksi data baru.

### Hasil
| Metrik | Nilai |
|---|---|
| Akurasi (data uji) | **≈ 97,37%** |
| Kedalaman pohon akhir | 4 |

---

## 📈 2. Linear Regression

**Notebook:** [`Linear_Regression.ipynb`](Linear_Regression.ipynb)
**Dataset:** data mini di dalam notebook & [`botak.csv`](botak.csv)

### Bagian A: Regresi Linear Sederhana
Memprediksi variabel `y` dari satu variabel `x` (8 data contoh, misalnya tinggi dan berat badan).

- Korelasi `x` dan `y`: **≈ 0,977** (sangat kuat)
- Koefisien: **≈ 0,68**
- Intercept: **≈ -39,37**
- Visualisasi: scatter plot data asli beserta garis regresi.

### Bagian B: Regresi Linear Berganda (`botak.csv`)
Memprediksi `botak_prob` (probabilitas kebotakan, rentang 0 sampai 1) dari beberapa fitur numerik.

**Dataset:** 7.991 baris, 13 kolom.

| Kolom | Keterangan |
|---|---|
| `umur`, `gaji`, `tinggi`, `berat` | Fitur numerik **yang dipakai model** |
| `jenis_kelamin`, `pekerjaan`, `provinsi`, `sampo`, `pendidikan` | Fitur kategorikal (belum dipakai) |
| `is_menikah`, `is_keturunan`, `is_merokok` | Fitur biner (belum dipakai) |
| `botak_prob` | **Target** |

**Alur kerja:**
1. Cek tipe data dan korelasi antar fitur numerik (heatmap `seaborn`).
2. Hapus baris yang memiliki nilai kosong pada kolom `umur`, `gaji`, `tinggi`, `berat`, dan `botak_prob`.
3. Split data: 80% latih, 20% uji (`random_state=0`).
4. Latih `LinearRegression`, lalu evaluasi dengan MSE dan R².
5. Visualisasi nilai asli vs nilai prediksi.

**Hasil:**

| Metrik | Nilai |
|---|---|
| MSE | ≈ 0,0318 |
| R² Score | ≈ 0,109 |

> 💡 **Catatan:** Nilai R² yang rendah menunjukkan keempat fitur numerik saja belum cukup menjelaskan `botak_prob`. Ruang untuk pengembangan: memanfaatkan fitur kategorikal (*one-hot encoding*), menangani *missing value* dengan imputasi, atau mencoba model non-linear seperti Random Forest / Gradient Boosting.

---

## 🛠️ Teknologi

- Python 3.8+
- [NumPy](https://numpy.org/)
- [pandas](https://pandas.pydata.org/)
- [Matplotlib](https://matplotlib.org/)
- [seaborn](https://seaborn.pydata.org/)
- [scikit-learn](https://scikit-learn.org/)
- Jupyter Notebook

## 🚀 Cara Menjalankan

1. **Clone repositori**
   ```bash
   git clone https://github.com/masean24/202431033_Raihan-Daris_Prak3_PEMSIN.git
   cd 202431033_Raihan-Daris_Prak3_PEMSIN
   ```

2. **(Opsional) Buat virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate      # Linux/macOS
   venv\Scripts\activate         # Windows
   ```

3. **Install dependensi**
   ```bash
   pip install numpy pandas matplotlib seaborn scikit-learn notebook
   ```

4. **Jalankan Jupyter Notebook**
   ```bash
   jupyter notebook
   ```
   Lalu buka `Decision Tree.ipynb` atau `Linear_Regression.ipynb`.

> Pastikan file CSV berada di folder yang sama dengan notebook, karena notebook membacanya dengan path relatif.

---

## 📚 Yang Dipelajari

- Pre-processing data (encoding label, penanganan *missing value*)
- Pembagian data latih dan data uji (`train_test_split`)
- Klasifikasi dengan Decision Tree dan visualisasi pohonnya
- Regresi linear sederhana dan berganda
- Evaluasi model: akurasi, MSE, dan R²
- Visualisasi data dan hasil model

## 📄 Lisensi

Proyek ini dibuat untuk keperluan pembelajaran (praktikum).

## 👤 Penulis

**Raihan Daris** (NIM 202431033): [@masean24](https://github.com/masean24)
