<div align="center">

# 🎵 Spotify Tracks Audio Profiling & K-Means Clustering
### *Unsupervised Machine Learning, Exploratory Data Analysis & Music Mood Segmentation*

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/dekbintang/data-mining/blob/main/Spotify_Dataset_Profiling2.ipynb)
[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![Scikit-Learn](https://img.shields.io/badge/scikit--learn-K--Means-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data_Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

<p align="center">
  Implementasi riset data mining komprehensif berbasis metodologi CRISP-DM pada dataset <b>Spotify Tracks (114.000 observasi)</b>. Mengintegrasikan Exploratory Data Analysis (EDA), normalisasi fitur akustik, segmentasi musik berbasis karakteristik emosional (*vibe/mood*) menggunakan algoritma K-Means ($k=4$), serta reduksi dimensi PCA 2D dan evaluasi <i>Russell's Circumplex Model</i>.
</p>

</div>

---

## ⚡ Eksekusi Interaktif (Google Colab)

Notebook penelitian ini dapat langsung dieksekusi tanpa konfigurasi lokal melalui Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/dekbintang/data-mining/blob/main/Spotify_Dataset_Profiling2.ipynb)

---

## 🏗️ Struktur dan Metodologi Analisis (CRISP-DM)

Alur penelitian mengacu pada metodologi baku *Cross-Industry Standard Process for Data Mining* (CRISP-DM):

### Bagian I: Exploratory Data Analysis (EDA)
1. **Pemuatan Pustaka dan Dataset**: Penyiapan lingkungan analisis (Pandas, NumPy, Scikit-Learn, Matplotlib, Seaborn).
2. **Identifikasi Struktur Data**: Pengecekan dimensi dataset, tipe data tiap atribut, dan pratinjau observasi.
3. **Statistik Deskriptif**: Perhitungan ukuran pemusatan (*mean*, median) dan penyebaran (*standard deviation*, kuartil).
4. **Evaluasi Kualitas Data**: Audit terhadap *missing values*, duplikasi data, konsistensi format, dan pencilan (*outliers*).
5. **Analisis Relasi Antarvariabel**: Visualisasi distribusi univariat, korelasi bivariat, dan pola multivariat.
6. **Sintesis Temuan EDA**: Rangkuman karakteristik distribusi data sebelum tahap transformasi.

### Bagian II: Data Preprocessing
7. **Pembersihan Data (*Data Cleaning*)**: Eliminasi entri *null*, deduplikasi berbasis `track_id` dan kombinasi `track_name` & `artists`, serta penyaringan rekaman dengan durasi tidak valid.
8. **Pemilihan Fitur (*Feature Selection*)**: Seleksi 9 atribut audio kontinu yang merepresentasikan karakter akustik dan emosional lagu (`danceability`, `energy`, `loudness`, `speechiness`, `acousticness`, `instrumentalness`, `liveness`, `valence`, `tempo`).
9. **Standarisasi Fitur (*Feature Scaling*)**: Transformasi menggunakan `StandardScaler` (z-score) untuk mencegah dominasi atribut berorde besar dalam kalkulasi jarak Euclidean.
10. **Verifikasi Data Siap Pemodelan**: Pengujian akhir distribusi mean dan standar deviasi matriks fitur terstandarisasi.

### Bagian III: Pemodelan Clustering dan Profiling Mood
11. **Optimasi Jumlah Klaster ($k$)**: Evaluasi matematis menggunakan *Elbow Method* (*Within-Cluster Sum of Squares* / WCSS) dan *Silhouette Analysis*, diselaraskan dengan model psikologi musik *Russell's Circumplex Model*.
12. **Pelatihan Algoritma K-Means**: Penerapan algoritma dengan inisialisasi `k-means++` dan parameter optimal ($k=4$).
13. **Reduksi Dimensi (PCA 2D)**: Proyeksi ruang fitur 9 dimensi ke dalam 2 komponen utama (*Principal Components*) untuk visualisasi sebaran spasial dan posisi *centroid*.
14. **Profiling Karakteristik Klaster**: Pemetaan nilai rata-rata atribut audio per klaster menggunakan visualisasi *Radar Chart* dan matriks numerik.
15. **Interpretasi dan Pelabelan Klaster**: Kategorisasi klaster ke dalam kelompok *mood* musik yang representatif beserta sampel observasi teratas.
16. **Validasi Silang Distribusi Genre**: Analisis kesesuaian antara klaster yang terbentuk secara *unsupervised* dengan label genre asli pada dataset.
17. **Kesimpulan Penelitian**: Rangkuman temuan analitis dan implikasi manajerial untuk sistem rekomendasi musik (*Recommendation Engine*).

---

## 🛠️ Persyaratan Lingkungan (*Environment Requirements*)

Proyek ini memerlukan dependensi Python berikut:

- Python 3.8+
- `pandas` >= 1.3.0
- `numpy` >= 1.20.0
- `scikit-learn` >= 1.0.0
- `matplotlib` >= 3.4.0
- `seaborn` >= 0.11.0

---

## ⚡ Petunjuk Penggunaan

### 1. Eksekusi Lokal
1. Clone repositori ini:
   ```bash
   git clone https://github.com/dekbintang/data-mining.git
   cd data-mining
   ```
2. Buka notebook menggunakan Jupyter Lab atau VS Code:
   ```bash
   jupyter notebook Spotify_Dataset_Profiling2.ipynb
   ```
3. Jalankan seluruh sel secara berurutan (*Run All*).

### 2. Eksekusi Cloud (Google Colab)
1. Klik tombol **Open In Colab** di atas.
2. Pilih menu **Runtime** $\rightarrow$ **Run all**.

---

## 👨‍💻 Peneliti / Pengembang

**I Kadek Bintang Adi Bimantara**  
*Program Studi Teknologi Informasi — Universitas Udayana*  
* [GitHub Profile](https://github.com/dekbintang)
* [Instagram](https://instagram.com/ikadek_bintang)

---

## 📄 Lisensi
Proyek ini dilisensikan di bawah [Lisensi MIT](LICENSE). Bebas digunakan dan dikembangkan untuk keperluan riset dan akademis.
