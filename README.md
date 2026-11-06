# Spotify Tracks Audio Clustering

Proyek data mining pada dataset Spotify Tracks (114.000 observasi). Implementasi EDA, preprocessing, dan segmentasi musik berdasarkan karakteristik audio menggunakan K-Means.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/dekbintang/data-mining/blob/main/Spotify_Dataset_Profiling2.ipynb)

## Tech Stack

- Python 3.8+, Pandas, NumPy, Scikit-Learn, Matplotlib, Seaborn

## Metodologi (CRISP-DM)

**Bagian I — EDA:**
Struktur data, statistik deskriptif, audit missing values & duplikasi, analisis korelasi.

**Bagian II — Preprocessing:**
Eliminasi null & duplikat, seleksi 9 fitur audio kontinu, standarisasi z-score.

**Bagian III — Clustering:**
Optimasi jumlah klaster (Elbow Method + Silhouette Analysis), K-Means dengan k=4, reduksi dimensi PCA 2D, profiling klaster via Radar Chart, pelabelan mood, dan validasi silang genre.

## Setup

```bash
git clone https://github.com/dekbintang/data-mining.git
cd data-mining
jupyter notebook Spotify_Dataset_Profiling2.ipynb
```

Atau langsung eksekusi via [Google Colab](https://colab.research.google.com/github/dekbintang/data-mining/blob/main/Spotify_Dataset_Profiling2.ipynb).

## Lisensi

[MIT](LICENSE)
