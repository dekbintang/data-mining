# Analisis Data Mining: Profiling, Preprocessing, dan Clustering Spotify Tracks Dataset

Repositori ini memuat implementasi proyek data mining menggunakan dataset *Spotify Tracks* (114.000 observasi). Fokus penelitian mencakup *Exploratory Data Analysis* (EDA), *Data Preprocessing*, serta segmentasi musik berbasis karakteristik audio (*vibe/mood*) menggunakan algoritma *Unsupervised Learning* K-Means.

---

## Tautan Google Colab

Proyek ini dapat dieksekusi secara interaktif melalui tautan Google Colab berikut:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/dekbintang/data-mining/blob/main/Spotify_Dataset_Profiling2.ipynb)

---

## Struktur dan Metodologi Analisis

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
8. **Pemilihan Fitur (*Feature Selection*)**: Seleksi 9 atribut audio kontinu yang merepresentasikan karakter akustik dan emosional lagu.
9. **Standarisasi Fitur (*Feature Scaling*)**: Transformasi menggunakan `StandardScaler` (z-score) untuk mencegah dominasi atribut berorde besar dalam kalkulasi jarak Euclidean.
10. **Verifikasi Data Siap Pemodelan**: Pengujian akhir distribusi mean dan standar deviasi matriks fitur terstandarisasi.

### Bagian III: Pemodelan Clustering dan Profiling Mood
11. **Optimasi Jumlah Klaster ($k$)**: Evaluasi matematis menggunakan *Elbow Method* (*Within-Cluster Sum of Squares* / WCSS) dan *Silhouette Analysis*, diselaraskan dengan model psikologi musik *Russell's Circumplex Model*.
12. **Pelatihan Algoritma K-Means**: Penerapan algoritma dengan inisialisasi `k-means++` dan parameter optimal ($k=4$).
13. **Reduksi Dimensi (PCA 2D)**: Proyeksi ruang fitur 9 dimensi ke dalam 2 komponen utama (*Principal Components*) untuk visualisasi sebaran spasial dan posisi *centroid*.
14. **Profiling Karakteristik Klaster**: Pemetaan nilai rata-rata atribut audio per klaster menggunakan visualisasi *Radar Chart* dan matriks numerik.
15. **Interpretasi dan Pelabelan Klaster**: Kategorisasi klaster ke dalam kelompok *mood* musik yang representatif beserta sampel observasi teratas.
16. **Validasi Silang Distribusi Genre**: Analisis kesesuaian antara klaster yang terbentuk secara *unsupervised* dengan label genre asli pada dataset.
17. **Kesimpulan Penelitian**: Rangkuman temuan analitis dan implikasi manajerial untuk sistem rekomendasi musik.

---

## Persyaratan Lingkungan (*Environment Requirements*)

Proyek ini memerlukan dependensi Python berikut:

- Python 3.8+
- pandas >= 1.3.0
- numpy >= 1.20.0
- scikit-learn >= 1.0.0
- matplotlib >= 3.4.0
- seaborn >= 0.11.0

---

## Petunjuk Penggunaan

1. **Eksekusi Lokal**:
   - Gandakan repositori ini: `git clone https://github.com/dekbintang/data-mining.git`
   - Buka notebook menggunakan Jupyter Lab atau VS Code: `jupyter notebook Spotify_Dataset_Profiling2.ipynb`
   - Jalankan sel secara berurutan (*Run All*).

2. **Eksekusi Cloud (Google Colab)**:
   - Klik tombol **Open In Colab** di atas.
   - Pilih menu **Runtime** $\rightarrow$ **Run all**.
   - Simpan hasil eksekusi kembali ke repositori melalui menu **File** $\rightarrow$ **Save a copy in GitHub**.
