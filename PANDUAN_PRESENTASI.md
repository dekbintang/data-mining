# Panduan Presentasi Proyek Data Mining: Spotify Tracks Dataset

Dokumen ini disusun sebagai panduan terstruktur dan ringkas untuk mempresentasikan proyek data mining di hadapan dosen penguji atau pembimbing.

---

## 1. Identitas Proyek
- **Judul Proyek**: Profiling, Preprocessing, dan Clustering Spotify Tracks Dataset Berbasis Karakteristik Audio Kontinu
- **Dataset**: Spotify Tracks Dataset (114.000 rekaman lagu, 20 atribut)
- **Metodologi**: CRISP-DM (*Cross-Industry Standard Process for Data Mining*)
- **Algoritma Utama**: K-Means Clustering (*Unsupervised Learning*) didukung *Principal Component Analysis* (PCA)

---

## 2. Alur Presentasi Terstruktur (Estimasi 5 - 7 Menit)

### Tahap 1: Pendahuluan dan Latar Belakang (1 Menit)
- **Masalah**: Platform streaming musik modern memiliki jutaan lagu. Rekomendasi musik konvensional sering kali hanya mengandalkan genre teks, padahal lagu dengan genre sama bisa memiliki suasana hati (*mood*) yang bertolak belakang (misalnya: lagu rock lambat/akustik vs rock bertempo tinggi).
- **Tujuan**: Membangun model segmentasi musik berbasis karakteristik audio murni tanpa label (*unsupervised*) untuk mengelompokkan musik ke dalam klaster *mood/vibe* yang objektif.

### Tahap 2: Data Understanding dan Preprocessing (1.5 Menit)
- **Karakteristik Data Awal**: 114.000 observasi dan 20 atribut.
- **Pembersihan Data**:
  - Penanganan nilai *null* pada atribut metadata (`artists`, `album_name`, `track_name`).
  - Eliminasi duplikasi observasi berdasarkan `track_id` serta kombinasi nama lagu dan artis.
  - Penapisan durasi lagu anomali (< 30 detik) yang umumnya merupakan rekaman *white noise* atau efek suara.
- **Feature Selection**: Memilih 9 atribut audio kontinu yang relevan terhadap karakter musik: `danceability`, `energy`, `loudness`, `speechiness`, `acousticness`, `instrumentalness`, `liveness`, `valence`, dan `tempo`.
- **Feature Scaling**: Menerapkan `StandardScaler` (z-score) sehingga setiap atribut memiliki rata-rata = 0 dan standar deviasi = 1.

### Tahap 3: Pemodelan dan Penentuan Hiperparameter (1.5 Menit)
- **Justifikasi Nilai $k = 4$**:
  1. *Elbow Method*: Titik infleksi laju penurunan inersia (*WCSS*) mulai melandai pada rentang $k = 4$ hingga 5.
  2. *Silhouette Coefficient*: Skor pemisahan klaster menunjukkan nilai yang stabil dan memadai.
  3. *Russell's Circumplex Model of Affect*: Dalam literatur psikologi musik, emosi musik dimodelkan secara universal ke dalam 4 kuadran afeksi berdasarkan sumbu *Valence* (positif/negatif) dan *Arousal/Energy* (tinggi/rendah).

### Tahap 4: Hasil Analisis dan Profiling Klaster (1.5 Menit)
- **Visualisasi PCA (2D Projection)**: Mereduksi 9 dimensi ke 2 komponen utama untuk memvalidasi sebaran spasial dan pemisahan titik *centroid*.
- **Radar Chart Profil Karakteristik**:
  - **Klaster 0 (High Energy & Danceable)**: `danceability` dan `energy` tinggi, `loudness` kuat. Merepresentasikan suasana pesta, olahraga, dan festival.
  - **Klaster 1 (Acoustic & Low Arousal)**: `acousticness` sangat dominan, `energy` rendah. Merepresentasikan musik instrumental, tidur, dan relaksasi.
  - **Klaster 2 (Melancholic & Low Valence)**: `valence` paling rendah, energi moderat/rendah. Merepresentasikan suasana reflektif, sedih, atau melankolis.
  - **Klaster 3 (Upbeat & High Valence)**: `valence` dan `danceability` sangat tinggi. Merepresentasikan nuansa riang, ceria, dan bersemangat (*feel-good pop*).
- **Validasi Silang dengan Genre Asli**: Genre seperti *dance*, *club*, dan *edm* terkonsentrasi di Klaster 0; genre *acoustic* dan *classical* di Klaster 1. Ini membuktikan model mampu mengelompokkan musik secara alami tanpa supervisi label.

### Tahap 5: Kesimpulan dan Manfaat Terapan (0.5 Menit)
- Segmentasi berbasis audio ini dapat diimplementasikan sebagai mesin rekomendasi playlist personal berbasis suasana hati (*mood-based playlist generation*).

---

## 3. Antisipasi Pertanyaan Dosen Penguji dan Jawaban Konseptual

### Pertanyaan 1: Mengapa menggunakan algoritma K-Means, bukan algoritma clustering lain seperti Hierarchical Clustering atau DBSCAN?
**Jawaban**:
> *"K-Means dipilih karena memiliki kompleksitas komputasi linear terhadap jumlah observasi, yaitu $\mathcal{O}(n \cdot k \cdot i)$, sehingga sangat efisien dan terukur untuk dataset berukuran besar (114.000 observasi). Sebagai perbandingan, Hierarchical Clustering memiliki kompleksitas ruang dan waktu $\mathcal{O}(n^2)$ yang membutuhkan komputasi matriks jarak sebesar lebih dari 12 miliar elemen, yang rentan menyebabkan Out of Memory (OOM) pada mesin standar."*

### Pertanyaan 2: Mengapa standarisasi fitur (StandardScaler) wajib dilakukan sebelum K-Means?
**Jawaban**:
> *"K-Means mengukur kedekatan antartitik berdasarkan jarak Euclidean. Atribut audio memiliki satuan dan rentang nilai yang sangat heterogen; misalnya `tempo` bernilai antara 50 hingga 240 BPM dan `loudness` bernilai negatif dalam desibel, sementara `valence` hanya berkisar 0 hingga 1. Tanpa standarisasi, atribut berskala besar akan mendominasi perhitungan jarak, sehingga atribut bernilai kecil menjadi tidak berpengaruh. StandardScaler mentransformasikan seluruh atribut ke skala z-score yang setara (mean = 0, std = 1)."*

### Pertanyaan 3: Apa fungsi Principal Component Analysis (PCA) dalam proyek ini? Apakah PCA dilakukan sebelum atau sesudah pelatihan model?
**Jawaban**:
> *"Pelatihan model K-Means dilakukan secara penuh pada seluruh 9 atribut audio asli yang telah distandarisasi untuk mempertahankan 100% informasi data. PCA dengan 2 komponen utama di sini digunakan secara khusus sebagai **metode proyeksi visualisasi 2D**, karena representasi ruang berdimensi 9 tidak dapat diamati secara langsung oleh mata manusia."*

### Pertanyaan 4: Mengapa tidak menyertakan atribut `popularity` dan `track_genre` ke dalam matriks clustering?
**Jawaban**:
> *"Tujuan pemodelan adalah mengelompokkan musik berdasarkan **sifat intrinsik akustik audio**, bukan faktor eksternal pasar. `popularity` merupakan metrik bisnis yang berubah seiring waktu dan tidak mencerminkan karakter musik. Sedangkan `track_genre` sengaja diisolasi untuk dijadikan **variabel pengujian eksternal (cross-validation)** guna menilai apakah klaster unsupervised yang terbentuk selaras dengan klasifikasi genre musik yang sebenarnya."*

