### Klasifikasi Kesegaran Buah Menggunakan Perbandingan CNN Kustom dan MobileNetV2

### **Nama Anggota Kelompok:**
* **Kelompok:** Blekpink
* **Anggota:**
  1. [Calya Alesita Putri Irawan] - [103132400020]
  2. [Isna Farhah Umami] - [103132430004]
  3. [Balqis Awaluna Rahmah] - [103132430011]

### **Deskripsi Permasalahan:**
Dalam industri pangan dan manajemen supermarket, menjaga kualitas buah sangat penting karena buah mudah sekali membusuk. Masalahnya, proses pemilahan antara buah segar (*fresh*) dan buah busuk (*rotten*) saat ini sebagian besar masih dilakukan secara manual menggunakan tenaga manusia. 

Proses manual ini memiliki beberapa kekurangan utama:
* **Faktor Kelelahan:** Ketelitian manusia pasti menurun setelah bekerja berjam-jam, sehingga rawan terjadi kesalahan sortir buah.
* **Penilaian Subjektif:** Standar kesegaran buah bisa berbeda-beda dan tidak konsisten antara pekerja satu dengan yang lain.
* **Kurang Efisien:** Memakan waktu yang lama dan biaya operasional yang besar jika volume buah sangat banyak.

Untuk mengatasi masalah tersebut, proyek kelompok kami memanfaatkan teknologi *Computer Vision* berbasis *Machine Learning*. Kami membangun sistem berbasis kecerdasan buatan (AI) yang mampu mengidentifikasi kondisi buah (Apel, Pisang, dan Jeruk) secara otomatis melalui kamera. Sistem ini akan menganalisis visual buah lalu mengelompokkannya ke dalam kategori **Fresh** atau **Rotten** agar proses penyortiran bisa berjalan jauh lebih cepat, konsisten, dan akurat.

### **Sumber dan Deskripsi Dataset:**
* **Sumber Dataset:** Dataset terbuka dari platform Kaggle dengan judul *"Fruits Fresh and Rotten for Classification"*.
* **Deskripsi Dataset:** Dataset ini berisi gambar-gambar buah yang terbagi menjadi beberapa kelas kategori visual, yaitu: `freshapples`, `freshbananas`, `freshoranges`, `rottenapples`, `rottenbananas`, dan `rottenoranges`.
* **Pembagian Data:** Dataset sudah dipisahkan ke dalam folder `train/` untuk melatih ingatan model AI dan folder `test/` untuk menguji performa keakuratan akhir model.

### **Tahapan Preprocessing:**
Sebelum gambar dimasukkan ke dalam model pelatihan AI, data melalui beberapa tahapan transformasi agar siap diproses:
1. **Penyetaraan Ukuran (Resize):** Mengubah semua ukuran dimensi foto gambar buah menjadi standar yang sama, yaitu `224 x 224` piksel.
2. **Normalisasi Piksel (Rescale):** Mengubah nilai piksel warna gambar asli dari rentang 0-255 menjadi rentang 0-1 agar proses komputasi model menjadi lebih ringan dan cepat.
3. **Augmentasi Data:** Khusus untuk data latihan (*training*), gambar dimodifikasi secara otomatis seperti diputar balik (*horizontal flip*), digeser (*shear range*), dan diperbesar (*zoom range*). Proses ini bertujuan untuk memperkaya variasi data agar model tidak mengalami *overfitting*.

### **Metode yang Digunakan:**
Untuk mendapatkan hasil yang paling optimal, kelompok kami membandingkan dua arsitektur *Deep Learning* sekaligus:
1. **Model CNN Kustom (Sequential):** Model jaringan saraf konvolusional standar yang kami rancang sendiri struktur lapisannya dari awal menggunakan beberapa layer `Conv2D`, `MaxPooling2D`, `Flatten`, serta `Dropout` untuk mencegah ketergantungan data.
2. **Transfer Learning (MobileNetV2):** Memanfaatkan arsitektur canggih *pre-trained model* MobileNetV2 yang aslinya sudah dilatih oleh Google pada jutaan gambar lain. Kami memodifikasi lapisan outputnya agar sesuai untuk mengklasifikasikan kelas buah segar dan busuk.

### **Cara Menjalankan Program:**
1. Unduh dataset gambar buah dari Kaggle, lalu unggah folder `train` dan `test` tersebut ke Google Drive kelompok kalian.
2. Buka file notebook proyek `Klasifikasi_Buah.ipynb` melalui Google Colab.
3. Pastikan jenis *hardware* sudah diubah ke GPU gratis bawaan Google (*Runtime > Change runtime type > T4 GPU*).
4. Jalankan baris kode pertama untuk menghubungkan (*mount*) Google Colab dengan Google Drive, lalu sesuaikan jalur alamat (*path*) foldernya.
5. Jalankan semua baris kode dari atas sampai bawah secara berurutan (*Runtime > Run all*).

### **Hasil Eksperimen dan Evaluasi:**
Berdasarkan pengujian pada data uji (*test data*), berikut adalah performa dari kedua model:

* **Akurasi Akhir Model CNN Kustom:** 83,67%
* **Akurasi Akhir Model MobileNetV2:** 96,74%

#### 1. Evaluasi Model CNN Kustom
Model buatan sendiri ini menghasilkan performa yang cukup baik dengan rata-rata *F1-score* sebesar 0,84. Nilai terbaik didapatkan pada kelas `freshbananas` (F1-score: 0,98), sementara model masih sedikit kesulitan membedakan kelas `freshoranges` karena nilai *recall*-nya berada di angka 0,63 (banyak buah jeruk segar yang salah tertebak sebagai jeruk busuk).

#### 2. Evaluasi Model MobileNetV2
Model *Transfer Learning* berbasis MobileNetV2 menunjukkan performa yang sangat luar biasa dan presisi. Rata-rata nilai *F1-score* mencapai 0,97. Model ini hampir sempurna dalam mengenali seluruh kelas gambar buah, dengan nilai F1-score tertinggi pada kelas `freshapples` dan `freshbananas` yang menyentuh angka 0,99. Kesalahan tebakan pada *Confusion Matrix* model ini sangat minim di semua kelas.

### **Kesimpulan:**
Berdasarkan hasil eksperimen pengerjaan tugas besar kelompok Blekpink, pengujian klasifikasi kesegaran buah menggunakan metode **Transfer Learning MobileNetV2** terbukti memberikan performa akurasi yang jauh lebih tinggi (96,74%) dan proses konvergensi pelatihan yang lebih cepat dibandingkan dengan model CNN Kustom buatan sendiri (83,67%). Hal ini menunjukkan bahwa pemanfaatan bobot yang sudah terlatih (*pre-trained weights*) dari model skala industri sangat efektif digunakan untuk mendeteksi objek visual buah secara akurat dan konsisten.

### Dataset
Dataset yang digunakan pada proyek ini tersedia pada Google Drive berikut:
https://drive.google.com/drive/folders/1rbCkGI6CGM8pCf0x5WNljrSnkyJPNpM9?usp=drive_link

#### Citation
Kalluri, S. R. *Fruits Fresh and Rotten for Classification*. Kaggle Dataset.
https://www.kaggle.com/datasets/sriramr/fruits-fresh-and-rotten-for-classification
