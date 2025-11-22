Data Cleaning dan Penskalaan Kondisional

Ini adalah proyek inti untuk implementasi pipeline pembersihan data, yang berfokus pada pemuatan, pemeriksaan, dan penerapan logika penskalaan kondisional pada fitur-fitur numerik dalam dataset. Tujuannya adalah untuk memastikan konsistensi dan integritas data sebelum digunakan untuk analisis lebih lanjut atau pemodelan Machine Learning.

Fitur Utama

Pemuatan Data: Membaca data dari format file Excel (.xlsx) ke dalam DataFrame Pandas.

Pemeriksaan Awal: Analisis data awal untuk mengidentifikasi tipe data, nilai yang hilang, dan struktur kolom.

Pembersihan Bersyarat (Conditional Cleaning): Menerapkan fungsi kustom untuk mengoreksi potensi kesalahan unit atau skala pada kolom fitur utama.

Penskalaan Otomatis: Logika ini berfokus pada penyesuaian nilai yang tampaknya salah skala secara otomatis.

Arsitektur Sistem

Aliran data di dalam pipeline pembersihan ini sangat linier:

Tahap

Input

Proses Utama

Output

1. Inisialisasi

pivot_55_description_640rows(2).xlsx

Pemuatan file ke Pandas DataFrame.

DataMentah (Raw DataFrame)

2. Pembersihan Inti

Kolom AA1, AA2, AA3, AA4, AA5

Fungsi divide_by_1000 diterapkan.

DataBersih (Cleaned DataFrame)

3. Finalisasi

DataBersih

Pengecekan statistik dan konfirmasi.

DataSiap (Ready-for-Analysis Data)

Logika Penskalaan

Proyek ini mendefinisikan dan menerapkan fungsi penskalaan kustom yang bertujuan untuk memperbaiki potensi unit errors di mana nilai seharusnya berada dalam kisaran yang lebih kecil.

Aturan Penerapan

Logika ini hanya diterapkan pada kolom AA1 hingga AA5.

# Logika utama penskalaan kondisional:
# Jika nilai > 10, bagi nilai tersebut dengan 1000.
def divide_by_1000(value):
    if value > 10:
        return value / 1000
    return value


Penerapan pada Kolom

Logika diterapkan secara element-wise ke setiap sel di kolom yang ditargetkan.

# Menerapkan fungsi ke semua kolom AA1 hingga AA5
columns_to_scale = ['AA1', 'AA2', 'AA3', 'AA4', 'AA5']
for col in columns_to_scale:
    df[col] = df[col].apply(divide_by_1000)


Struktur Proyek

Proyek ini terdiri dari satu Jupyter Notebook utama yang berisi semua langkah, dari pemuatan data hingga verifikasi akhir.

proyek_cleaning/

TYBAS_LIDIA.ipynb: Notebook utama yang berisi kode, analisis awal, definisi fungsi, dan penerapan penskalaan kondisional.

pivot_55_description_640rows(2).xlsx: File data input.

Penyiapan dan Instalasi

Prasyarat

Lingkungan Python 3.x

pandas

numpy

openpyxl (untuk membaca file Excel)

Jupyter Notebook atau JupyterLab

Langkah-langkah

Clone Repositori (Jika ini adalah repositori Git)

git clone <url-repositori-anda>
cd <nama-folder-proyek>


Instal Dependensi

pip install pandas numpy openpyxl


Cara Menjalankan

Pastikan file data Excel (pivot_55_description_640rows(2).xlsx) berada di direktori yang sama dengan notebook.

Buka notebook TYBAS_LIDIA.ipynb:

jupyter notebook TYBAS_LIDIA.ipynb


Jalankan semua sel di notebook untuk melihat setiap tahap pembersihan data, dari pemuatan hingga hasil akhir yang diskalakan.
