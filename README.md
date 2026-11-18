# Prediksi Harga Saham JECC dengan Linear Regression
## Tujuan 
Memprediksi harga penutupan jam berikutnya saham JECC (5.547 baris data per jam, 5.546 setelah target dibuat) April 2020 - Desember 2022, dari harga open, close, high, low, volume dengan Linear Regression

## Dataset 
Dataset diberikan oleh dosen mata kuliah Machine Learning. Kolom timestamp, open, high, low, close, volume. Data per jam (Timestamp) dari tanggal 16 April 2020 sampai 30 Desember 2022 dan 5.546 baris setelah target dibuat. 

## Metode
- Mengambil data dari dataset dengan Pandas 
- Melakukan pra-pemrosesan data pada kolom timestamp dan membuat sebuah variabel Target dengan menggunakan shift dalam kolom close
- Mengetahui nilai korelasi data dengan corr 
- Membuat variabel x (Fitur: open, close, high, low, volume) dan y (Target/Label: harga close jam berikutnya), dan split data train and test 80:20
- Model dan latih algoritma Linear Regression tanpa parameter tambahan
- Evaluasi dengan 9 metriks, prediksi, dan skor model (R2), nilai slope/koefisien (m) dengan coef dan intercept (b)
- Visualisasi data Residual plot (Grafik selisih prediksi dan nilai aktual) dan Scatter plot High vs Low dan Open vs Close hanya sebaran data
- Visualisasi Prediksi dan Aktual Harga Saham dilihat pada index dari kolom timestamp dan Harga saham dari prediksi

## Hasil
|     Evaluasi Model        |     Nilai    |
|---------------------------|--------------|
| Mean Squared Error (MSE)  | 38948,671624 |
| Mean Absolute Error (MAE) |   43,682338  |
|          RMSE             |  197,354178  |
|          RMAE             |   6,609262   |
|   R2 Score (model.score)  |   0,964173   |
|  Explained Variance Score |   0,964173   |
|     Mean Pinball Loss     |   21,841169  |
|     D2 Pinball Score      |   0,945946   |
|  D2 Absolute Error Score  |   0,945946   |

Prediksi vs Aktual:
![Prediksi vs Aktual](<Prediksi_vs_Aktual.png>)

## Cara Menjalankan (Jupyter Notebook)
```bash 
conda install pandas numpy seaborn matplotlib scikit-learn
cd Prediksi-Harga-Saham-JECC-Dengan-Linear-Regression-main
jupyter notebook
```
Buka file Prediksi_Harga_Saham.ipynb

## Catatan
- Koefisien terbesar pada harga close (0,87), artinya harga berikutnya sangat dipengaruhi harga terakhir.
- RMSE dan RMAE sebagai akar dari MSE dan MAE.
- Sebagai pembanding, tebakan sederhana pada harga jam berikutnya dengan harga jam sekarang (baseline) menghasilkan R2 0,9645 dan MAE (Mean Absolute Error) 28,46. MAE model ini (43,68) lebih besar dari baseline, jadi model ini belum lebih baik dari tebakan sederhana. 
- Data dibagi acak 80:20 padahal berurutan waktu. Dengan pembagian kronologis, nilai R2 turun menjadi sekitar 0,50.
