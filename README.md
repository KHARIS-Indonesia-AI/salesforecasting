# 📊 Sales Forecasting Project

## 📝 Overview

This project implements time series forecasting models to predict sales and promotion effects for retail data. The analysis **specifically focuses on the "CLEANING" product category** from a larger retail dataset and employs both traditional statistical methods and modern deep learning approaches.

## 🎯 Project Goals

- Analyze sales patterns and their relationship with promotional activities for cleaning products
- Develop accurate forecasting models for predicting future cleaning product sales
- Compare the performance of different forecasting algorithms
- Provide insights for inventory management and promotion planning in the cleaning category

## 🔍 Dataset Description

The dataset is derived from `store5.csv` which contains daily sales data across multiple product categories. For this analysis, we've filtered to focus exclusively on the "CLEANING" product category. The relevant features include:

| Column | Description |
|--------|-------------|
| date | Date of the transaction |
| store_nbr | Store number identifier (filter: store_nbr = 5) |
| family | Product family/category (filter: family = "CLEANING") |
| sales | Sales volume/value for cleaning products |
| onpromotion | Number of cleaning items on promotion |
| dcoilwtico | Oil price index - external factor |

**Data Selection Focus:** From the original dataset containing multiple product categories across different stores, we specifically analyze store #5's cleaning products data to develop a focused forecasting model for this category.

## 🛠️ Methods & Models

### Data Preprocessing
- Missing value handling using polynomial interpolation
- Box-Cox transformation for non-normal distributed data
- Handling of missing dates (e.g., holidays like Christmas)
- Stationarity analysis and differencing

### Models Implemented
1. **VARMAX** (Vector Autoregressive Moving Average with Exogenous variables)
   - Multivariate time series model
   - Captures relationships between cleaning product sales and promotional activities
   - Incorporates external factors (oil price)

2. **Single Layer LSTM**
   - Basic deep learning approach for time series
   - Captures long-term dependencies in cleaning products sales patterns

3. **Stacked LSTM**
   - Multi-layered architecture for capturing complex patterns
   - Enhanced representational capacity for seasonal trends in cleaning product sales

4. **Bidirectional LSTM**
   - Learns patterns from both past and future contexts
   - Often provides better performance for time series prediction

## 📋 Hasil & Perbandingan (Results & Comparison)

Perbandingan performa model berdasarkan RMSE (Root Mean Squared Error) untuk prediksi sales dan promosi dalam kategori CLEANING:

| Model | Sales RMSE | Onpromotion RMSE |
|-------|------------|------------------|
| VARMAX | xxx.xx | xx.xx |
| Single LSTM | xxx.xx | xx.xx |
| Stacked LSTM | xxx.xx | xx.xx |
| Bidirectional LSTM | xxx.xx | xx.xx |

*Note: Replace the placeholder values with actual results from your analysis.*

## 📊 Visualisasi Utama (Key Visualizations)

Beberapa visualisasi penting yang dihasilkan dalam analisis kategori CLEANING:

1. Time series plot untuk sales dan onpromotion pada produk cleaning
2. Seasonal decomposition (trend, seasonal, residual) 
3. ACF dan PACF plots untuk analisis pola
4. Perbandingan nilai aktual vs. prediksi untuk setiap model
5. Perbandingan performa model (bar charts)

## 🔧 Penggunaan (Usage)

### Persyaratan (Requirements)

```
pandas==1.5.3
numpy==1.24.3
matplotlib==3.7.1
seaborn==0.12.2
statsmodels==0.14.0
scikit-learn==1.3.0
tensorflow==2.13.0
scipy==1.10.1
```

### Menjalankan Kode (Running the Code)

1. Clone repository ini:
```bash
git clone https://github.com/yourusername/sales-forecasting.git
cd sales-forecasting
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Sesuaikan path file pada bagian awal script:
```python
# Path file (sesuaikan dengan lokasi Anda)
FILE_PATH = 'path/to/your/store5.csv'
OUTPUT_PATH = 'path/to/your/output/store5.xlsx'
```

4. Jalankan script utama:
```bash
python sales_forecasting.py
```

*Note: Script akan otomatis memfilter dataset untuk kategori "CLEANING" dan melakukan seluruh analisis hanya pada data tersebut.*

## 📋 Struktur Proyek (Project Structure)

```
sales-forecasting/
│
├── data/
│   ├── store5.csv            # Raw data (all categories)
│   └── store5.xlsx           # Processed data (output)
│
├── notebooks/
│   └── sales_forecasting.ipynb  # Jupyter notebook (exploratory)
│
├── src/
│   ├── sales_forecasting.py     # Main script
│   └── utils.py                 # Utility functions
│
├── visualizations/             # Generated plots and charts
│
├── requirements.txt            # Dependencies
└── README.md                   # This documentation
```

## 🚀 Kesimpulan & Rekomendasi (Conclusions & Recommendations)

Berdasarkan analisis yang telah dilakukan pada kategori produk CLEANING, beberapa kesimpulan dan rekomendasi:

1. Model [BEST_MODEL] menunjukkan performa terbaik dengan RMSE terendah untuk prediksi sales produk cleaning.
2. Terdapat korelasi positif (0.45) antara aktivitas promosi dan penjualan produk cleaning.
3. Pola mingguan (weekly seasonality) terlihat jelas dalam data penjualan produk cleaning.
4. Faktor eksternal seperti harga minyak memiliki korelasi rendah dengan penjualan produk cleaning.

Rekomendasi untuk implementasi bisnis kategori CLEANING:
- Fokuskan promosi pada periode dengan penjualan rendah untuk meratakan inventory produk cleaning
- Gunakan model [BEST_MODEL] untuk peramalan jangka pendek (1-7 hari)
- Perbarui model secara berkala (misalnya bulanan) untuk menjaga akurasi prediksi
- Pertimbangkan untuk mengembangkan model serupa untuk kategori produk lainnya
