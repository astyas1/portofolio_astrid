import pandas as pd
import matplotlib.pyplot as plt

file_path = '/mnt/data/sp500_trends.csv'
data = pd.read_csv(file_path)

print("\nPreview dataset:")
print(data.head())

print("\nInformasi dataset:")
data.info()

print("\nStatistik deskriptif:")
print(data.describe())

if 'Date' in data.columns and 'Close' in data.columns:
    # Pastikan kolom Date diformat sebagai datetime
    data['Date'] = pd.to_datetime(data['Date'])
    data.sort_values('Date', inplace=True)

    # Membuat plot harga penutupan
    plt.figure(figsize=(12, 6))
    plt.plot(data['Date'], data['Close'], label='Close Price', color='blue')
    plt.title('Tren Harga Penutupan S&P 500')
    plt.xlabel('Tanggal')
    plt.ylabel('Harga Penutupan')
    plt.legend()
    plt.grid()
    plt.show()
else:
    print("Kolom 'Date' atau 'Close' tidak ditemukan dalam dataset.")
