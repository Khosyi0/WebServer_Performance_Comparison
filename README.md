# Task
- Menggunakan program yang berada di lab progjar5 dan memodifikasi contoh source code yang disediakan. 
- Implementasikan web server menggunakan teknik multiprocessing, kemudian membandingkan kinerjanya dengan tiga skenario lainnya yaitu multithreading, multithreading dengan keamanan (secure), dan multiprocessing dengan keamanan (secure). 
- Ukur kinerja dengan jumlah request 1000 dan parameter concurrency 10, 50, 100, 150, 200. 

# Tools
Tool yang digunakan adalah `siege`, untuk menginstallnya dapat menggunakan command
```
sudo apt-get install siege
```

# Spek Laptop
```
Processor	: AMD Ryzen 7 5700U with Radeon Graphics            1.80 GHz
RAM 		: 16.0 GB (15.3 GB usable)
OS Used	 	: Windows 11
```

# Step Pengerjaan
- Lakukan `docker-compose up -d` di direktori `progjar/environtment` setelah mengcloning https://github.com/TamaFn/ETS-Progjar.git dan masuk ke localhost di browser
- Membuka dua tab pada browser, tab pertama berperan sebagai Server menggunakan mesin1. Tab kedua berperan sebagai Client menggunakan mesin2
- Lakukan pengujian

## Multithreading
Pada Server, jalankan perintah
```
python3 server_thread_http.py
```
dan pada Client jalankan perintah 
```
siege -r 100 -c 10 http://172.16.16.101:8889
```
- -r 100 	: repetition berjumlah 100
- -c 10 	: concurrency berjumlah 10
- Jumlah request	: 100 * 10 = 1000

Implementasikan menggunakan parameter concurrency lainnya.

## Secure Multithreading
Pada Server, jalankan perintah
```
python3 server_thread_http_secure.py
```
dan pada Client jalankan perintah 
```
siege -r 100 -c 10 https://172.16.16.101:8889
```
- -r 100 	: repetition berjumlah 100
- -c 10 	: concurrency berjumlah 10
- Jumlah request	: 100 * 10 = 1000

Implementasikan menggunakan parameter concurrency lainnya.

## Multiprocessing
Pada Server, jalankan perintah
```
python3 server_process_http.py
```
dan pada Client jalankan perintah 
```
siege -r 100 -c 10 http://172.16.16.101:8443
```
- -r 100 	: repetition berjumlah 100
- -c 10 	: concurrency berjumlah 10
- Jumlah request	: 100 * 10 = 1000

Implementasikan menggunakan parameter concurrency lainnya.


## Multiprocessing
Pada Server, jalankan perintah
```
python3 server_process_http_secure.py
```
dan pada Client jalankan perintah 
```
siege -r 100 -c 10 https://172.16.16.101:8443
```
- -r 100 	: repetition berjumlah 100
- -c 10 	: concurrency berjumlah 10
- Jumlah request	: 100 * 10 = 1000

Implementasikan menggunakan parameter concurrency lainnya.


### Hasil pengujian
| n/a | Jumlah Concurrency | Transaction | Availability | Elapsed Time | Data Transferred | Response Time | Transaction Rate | Throughput | Concurrency | Successful Transaction | Failed Transaction | Longest Transaction | Shortest Transaction |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Multithreading | 10 | 998 | 99.8 | 254.55 | 0.03 | 1.98 | 3.92 | 0 | 7.78 | 998 | 2 | 19.31 | 0.01 |
| Multithreading | 50 | 913 | 91.3 | 250.95 | 0.03 | 3.71 | 3.64 | 0 | 13.48 | 913 | 87 | 57.01 | 0 |
| Multithreading | 100 | 866 | 86.6 | 236.34 | 0.03 | 4.43 | 3.66 | 0 | 16.23 | 866 | 134 | 58.96 | 0.02 |
| Multithreading | 150 | 894 | 85.14 | 446.07 | 0.03 | 5.63 | 2 | 0 | 11.29 | 894 | 156 | 110.49 | 0.04 |
| Multithreading | 200 | 774 | 77.4 |	233.14 | 0.02 | 6.49 | 3.32 | 0 | 21.53 | 774 | 226 | 114.15 | 0.04 |
| Secure Multithreading | 10 | 978 | 97.8 | 445.75 | 0.03 | 3.04 | 2.19 | 0 | 6.67 | 978 | 22 | 21.08 | 0.02 |
| Secure Multithreading | 50 | 817 | 81.7 | 317.41 | 0.02 | 5.23 | 2.57 | 0	| 13.47 | 817 | 183 | 64.47 | 0.02 |
| Secure Multithreading | 100 | 758 | 75.8 | 290.16 | 0.02 | 4.87 | 2.61 | 0 | 12.72 | 758 | 242 | 35.62 | 0.02 |
| Secure Multithreading | 150 | 693 | 66 | 286.24 | 0.02 | 7.04 | 2.42 | 0 | 17.04 | 693 | 357 | 72.9 | 0.03 |
| Secure Multithreading | 200 | 519 | 51.9 | 280.52 | 0.02 | 8.72 | 1.85 | 0 | 16.13 | 519 | 481 | 66.33 | 0 |
| MultiProcessing | 10 | 983 | 98.3 | 273.07 | 0.03 | 1.63 | 3.6 | 0 | 5.87 | 983 | 17 | 19.07 | 0 |
| MultiProcessing | 50 | 966 | 96.6 | 242.15 | 0.03 | 1.77 | 3.99 | 0 | 7.07 | 966 | 34 | 72.71 | 0 |
| MultiProcessing | 100 | 869 | 86.9 | 285.55 | 0.03 | 3.21 | 3.04 | 0 | 9.76 | 869 | 131 | 58.17 | 0.01 |
| MultiProcessing | 150 | 911 | 86.76 | 303.5 | 0.03 | 3.84 | 3 | 0 | 11.54 | 911 | 139 | 67.17 | 0.01 |
| MultiProcessing | 200 | 824 | 82.4 | 234.49 | 0.02 | 3.98 | 3.51 | 0 | 13.99 | 824 | 176 | 63.06 | 0.01 |
| Secure MultiProcessing | 10 | 984 | 98.4 | 254.79 | 0.02 | 1.42 | 3.86 | 0 | 5.48 | 984 | 16 | 29.45 | 0.05 |
| Secure MultiProcessing | 50 | 896 | 89.6 | 202.46 | 0.03 | 3.2 | 4.43 | 0 | 14.16 | 896 | 104 | 60.38 | 0.05 |
| Secure MultiProcessing | 100 | 873 | 87.3 | 223.66 | 0.03 | 3.7 | 3.9 | 0 | 14.43 | 873 | 127 | 110.44 | 0.05 |
| Secure MultiProcessing | 150 | 825 | 78.57 | 184.71 | 0.02 | 4 | 4.47 | 0 | 17.88 | 825 | 225 | 82.45 | 0.05 |
| Secure MultiProcessing | 200 | 729 | 72.9 | 298.02 | 0.02 | 6.25 | 2.45 | 0 | 15.29 | 729 | 271 | 118.93 | 0.05 |


### Kesimpulan 
Dari data yang didapatkan, dapat dilihat bahwa Successful Transaction berada di rentang jumlah 519 hingga 998, tidak ada skenario yang menunjukkan Successful Transaction sempurna yaitu 1000. Lalu, terlihat bahwa skenario multiprocessing lebih unggul dibandingkan multithreading, terutama saat concurrency semakin tinggi. Pada skenario secure multithreading dan secure multiprocessing, terlihat bahwa waktu response cenderung lebih lambat dan jumlah successful transaction cenderung lebih rendah dibandingkan dengan skenario tanpa keamanan. 

Terdapat catata beberapa faktor yang dapat mempengaruhi hasil pengukuran kinerja:
- Spesifikasi Perangkat Hardware: Performa sebuah web server juga dipengaruhi oleh spesifikasi perangkat keras yang digunakan, termasuk prosesor, RAM, dan penyimpanan. Perangkat keras yang lebih kuat mampu menangani beban kerja yang lebih besar dengan lebih efisien.
- Koneksi: Kinerja web server juga dapat dipengaruhi oleh kecepatan koneksi dan latensi. Keterbatasan jaringan dapat membatasi throughput dan responsivitas server.
- Sistem Operasi: Pilihan sistem operasi yang digunakan untuk menjalankan web server juga dapat mempengaruhi kinerja. Berbagai sistem operasi memiliki karakteristik yang berbeda dalam menangani proses, memori, dan sumber daya lainnya.