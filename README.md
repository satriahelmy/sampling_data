# Sampling_data

Sampling data adalah sebuah script yang digunakan untuk mendownload sebuah data dan mengkonversinya menjadi data sampling dengan beberapa langkah.
- mendownload data xlsx
- mengkonversi data menjadi .csv
- menggabungkan beberapa file menjadi satu file
- melakukan sampling

Berikut penjelasan setiap baris kodenya

1. Mendownload data weather ke dalam folder data
```
wget -P data https://github.com/labusiam/dataset/raw/main/weather_data.xlsx
```

2. Memindahkan direktori ke direktori data
```
cd data
```

3. Mengkonversi data ```weather_data.xslx``` ke CSV menggunakan perintah ```in2csv```

```
in2csv weather_data.xlsx --sheet "weather_2014" > weather_2014.csv
in2csv weather_data.xlsx --sheet "weather_2015" > weather_2015.csv
```

4. Menggabungkan 2 file csv menjadi 1 file csv

```
csvstack weather_2014.csv weather_2015.csv > weather.csv
```

5. Menghapus file ```weather_data.xlsx```

```
rm weather_data.xlsx
```

6. Melakukan sampling sebanyak 0.3 dan menyimpannya ke file ```sample_weather.csv```

```
cat weather.csv | sample -r 0.3 > sample_weather.csv
```
