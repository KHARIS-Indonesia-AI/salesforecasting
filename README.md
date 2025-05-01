# Proyek Sales Forecasting - Kategori Cleaning

## Tentang Proyek

Hai! Ini adalah proyek saya untuk memprediksi penjualan produk kategori "CLEANING" menggunakan beberapa model machine learning dan deep learning. Proyek ini dibuat sebagai bagian dari pembelajaran saya tentang analisis time series dan forecasting.

## Dataset

Saya menggunakan dataset `store5.csv` yang berisi data penjualan harian. Untuk proyek ini, saya hanya fokus pada data produk kategori "CLEANING" saja. Dataset memiliki beberapa kolom penting:

- `date` - Tanggal transaksi
- `store_nbr` - Nomor toko (saya pakai toko nomor 5)
- `family` - Kategori produk (saya filter hanya "CLEANING")
- `sales` - Jumlah penjualan
- `onpromotion` - Jumlah item yang sedang promosi
- `dcoilwtico` - Harga minyak (sebagai faktor eksternal)

## Apa yang Saya Lakukan

### Preprocessing Data
- Mengatasi missing values dengan interpolasi polinomial
- Transformasi Box-Cox untuk data yang tidak normal
- Menangani tanggal yang hilang (misalnya hari Natal)
- Analisis stasioneritas dan differencing

### Model yang Saya Coba

1. **VARMAX**
   - Model statistik tradisional
   - Bisa menangkap hubungan antara sales dan promosi

2. **Single Layer LSTM**
   - Model deep learning dasar
   - Untuk mempelajari pola jangka panjang

3. **Stacked LSTM**
   - LSTM dengan beberapa layer
   - Untuk pola yang lebih kompleks

4. **Bidirectional LSTM**
   - LSTM dua arah
   - Biasanya performa lebih baik untuk forecasting

## Hasil Perbandingan Model

Berikut perbandingan RMSE (Root Mean Squared Error) untuk setiap model - nilai lebih kecil berarti prediksi lebih akurat:

| Model | Test RMSE Sales | Test RMSE Onpromotion | Train RMSE Onpromotion |
|-------|----------------|---------------------|---------------------|
| Bidirectional LSTM | 218.55 | 7.79 | 2.17 |
| Single LSTM | 230.57 | 7.80 | 2.22 |
| Stacked LSTM | 249.49 | 11.72 | 2.77 |
| VARMAX | 226.26 | 26.58 | - |

Berdasarkan hasil ini, **Bidirectional LSTM** menunjukkan performa terbaik dengan RMSE terendah untuk prediksi sales (218.55) dan RMSE terendah untuk prediksi onpromotion (7.79).

## Visualisasi yang Saya Buat

1. Plot time series sales dan onpromotion
2. Dekomposisi musiman (trend, seasonal, residual)
3. Plot ACF dan PACF untuk analisis pola
4. Perbandingan nilai aktual vs prediksi
5. Grafik perbandingan model

## Cara Menjalankan Kode Ini

### Yang Perlu Diinstall

```
pandas
numpy
matplotlib
seaborn
statsmodels
scikit-learn
tensorflow
scipy
```

### Langkah-Langkah

1. Install library yang diperlukan:
```
pip install pandas numpy matplotlib seaborn statsmodels scikit-learn tensorflow scipy
```

2. Pastikan file dataset tersedia:
```
store5.csv 
```

3. Sesuaikan path file di awal kode:
```python
FILE_PATH = '/path/ke/store5.csv'
OUTPUT_PATH = '/path/ke/output/store5.xlsx'
```

4. Jalankan kode:
```
# Di Jupyter atau Google Colab
%run sales_forecasting.py

# Atau di terminal
python sales_forecasting.py
```

## Apa yang Saya Pelajari

Dari proyek ini, saya belajar:

1. Cara preprocessing data time series
2. Metode analisis stasioneritas
3. Implementasi model VARMAX dan LSTM
4. Perbandingan performa model forecasting
5. Visualisasi data time series

## Kesimpulan

Berdasarkan analisis saya pada data kategori CLEANING:

1. Terdapat pola mingguan yang jelas dalam penjualan
2. Ada korelasi positif (0.45) antara promosi dan penjualan
3. Model **Bidirectional LSTM** memberikan hasil prediksi paling akurat, dengan RMSE terendah baik untuk prediksi sales maupun onpromotion
4. Harga minyak tidak terlalu berpengaruh terhadap penjualan produk cleaning
5. Model deep learning (terutama Bidirectional LSTM) secara signifikan lebih baik dalam memprediksi jumlah onpromotion dibandingkan model statistik tradisional (VARMAX)


---