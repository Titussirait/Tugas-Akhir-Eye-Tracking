# Tugas-Akhir-Eye-Tracking
merupakan penerapan teknologi pelacakan mata pada bidang pemrosesan gambar. Konsep dasarnya adalah menggabungkan data pergerakan mata dengan informasi visual dari sebuah gambar atau video untuk mendapatkan pemahaman yang lebih mendalam tentang bagaimana manusia berinteraksi dengan konten visual.

## Langkah-langkah eye tracking

### Import Library:
numpy as np: Mengimpor library NumPy untuk operasi numerik.
cv2: Mengimpor library OpenCV untuk pemrosesan citra.
argparse: Digunakan untuk membuat argumen baris perintah (tidak digunakan dalam kode ini).
os, sys, inspect: Digunakan untuk mengelola path file (tidak digunakan dalam kode ini).
image_utils as utils: Mengimpor modul image_utils yang berisi fungsi-fungsi tambahan (asumsikan sudah ada).
EyeTrackingLib as tracker: Mengimpor modul EyeTrackingLib yang berisi fungsi-fungsi untuk melacak mata (asumsikan sudah ada).

### Fungsi image_resize:
Fungsi ini digunakan untuk mengubah ukuran gambar.
Parameter width dan height menentukan lebar dan tinggi baru gambar.
Fungsi ini akan menghitung perbandingan aspek untuk menjaga proporsi gambar saat diubah ukurannya.

### Memuat Classifier dan Gambar:
face_cascade: Memuat classifier Haar Cascade untuk mendeteksi wajah.
eye_cascade: Memuat classifier Haar Cascade untuk mendeteksi mata.
detect_face: Menentukan apakah akan memprioritaskan deteksi wajah sebelum mencari mata.
image: Membaca gambar yang akan diproses.

### Konversi ke Grayscale dan Pengaturan Pelacakan Mata:
gray: Mengubah gambar menjadi grayscale untuk mempermudah pemrosesan.
tracker.showImage = True: Mengaktifkan tampilan gambar yang telah diproses dengan fitur yang terdeteksi.

### Deteksi Wajah:
faces: Mendeteksi wajah-wajah dalam gambar menggunakan classifier.
face_box: Menyimpan informasi bounding box (kotak pembatas) wajah terbesar.

### Deteksi Mata dalam Wajah:
Jika wajah terdeteksi, kode akan mencari mata dalam wilayah wajah.
Menentukan wilayah minat (ROI) untuk mencari mata.
Menggunakan fungsi tracker.find_eye_center untuk menemukan pusat mata dalam ROI.
Menggambar lingkaran untuk menandai pusat mata.

### Deteksi Mata Secara Langsung (jika tidak ada wajah):
Jika tidak ada wajah terdeteksi, kode akan langsung mencari mata dalam seluruh gambar.

### Menampilkan Hasil:
cv2.imshow: Menampilkan gambar hasil dengan mata yang telah ditandai.
cv2.waitKey: Menunggu tombol ditekan untuk menutup jendela.
cv2.destroyAllWindows(): Menutup semua jendela yang terbuka.

### Kode ini melakukan langkah-langkah berikut:

Membaca gambar.
Mencari wajah dalam gambar.
Jika wajah ditemukan, mencari mata dalam wilayah wajah.
Jika tidak ada wajah, mencari mata dalam seluruh gambar.
Menampilkan hasil dengan mata yang ditandai.
Kode ini mengasumsikan adanya modul image_utils dan EyeTrackingLib yang berisi fungsi-fungsi tambahan.
Path ke file classifier dan gambar perlu disesuaikan dengan lokasi file pada sistem Anda.
Fungsi tracker.find_eye_center kemungkinan besar menggunakan algoritma tertentu untuk mendeteksi pusat mata.

### Hasil dari Eye Tracking
![image](https://github.com/user-attachments/assets/d7ab7ca4-c0a7-4cf3-b700-0b1b9305bd6c)

# Eye Tracking Video
Kita dapat mendemonstrasikan pelacakan mata dan bola mata pada video library OpenCV dan modul tambahan EyeTrackingLib

## Langkah-langkah eye tracking video

### impor Library:
numpy as np: untuk operasi numerik.
cv2 (OpenCV): untuk pemrosesan citra digital.
argparse: untuk menangani argumen baris perintah (opsional).
image_utils as utils: modul tambahan berisi fungsi utilitas untuk gambar (diasumsikan sudah ada).
EyeTrackingLib as tracker: modul yang berisi fungsi untuk pelacakan mata (diasumsikan sudah ada).

### Pengaturan Argumen dan Pembacaan Video:
Kode ini memungkinkan input dari webcam atau video file.
Jika tidak ada argumen video yang diberikan, webcam digunakan secara default.

### Fungsi add_text dan image_resize (Opsional):
Fungsi add_text menambahkan teks ke gambar.
Fungsi image_resize mengubah ukuran gambar (tidak digunakan pada pemrosesan utama).

### Memuat Classifier dan Pengaturan Awal:
Memuat classifier Haar Cascade untuk deteksi wajah dari path tertentu (perlu disesuaikan).
Mengatur tracker.showImage (diduga untuk menampilkan gambar hasil di modul EyeTrackingLib).

### Loop Pemrosesan Video:
Looping untuk memproses setiap frame dari video.
Membaca frame dari kamera/video.
Konversi frame ke grayscale dan equalizeHist untuk meningkatkan kontras.

### Deteksi Wajah:
Menggunakan classifier Haar Cascade untuk mendeteksi wajah pada frame grayscale.
Jika wajah terdeteksi, bounding box wajah terbesar akan diambil.

### Deteksi Mata dalam Wajah (jika wajah ditemukan):
Jika wajah ditemukan, kode akan memproses area wajah untuk mencari mata.
Mendefinisikan region of interest (ROI) di sekitar area mata yang diasumsikan berada di bagian atas dan samping wajah.
Memanggil fungsi tracker.find_eye_center (diduga dari EyeTrackingLib) untuk menemukan pusat mata dalam ROI.
Menggambar persegi panjang di sekitar ROI dan lingkaran di pusat mata yang terdeteksi.

### Deteksi Mata Langsung (jika wajah tidak ditemukan - Opsional):
Jika wajah tidak terdeteksi (blok kode dikomentari), kode akan mencoba mencari mata di seluruh frame (kurang akurat).

### Menampilkan Hasil dan Keluar:
Menampilkan frame hasil dengan deteksi wajah/mata di jendela "Output".
Menunggu penekanan tombol 'q' untuk keluar.
Membersihkan resource kamera dan jendela OpenCV.

Kode ini bergantung pada modul EyeTrackingLib yang diasumsikan sudah ada dan berisi fungsi tracker.find_eye_center untuk menemukan pusat mata.
Path ke file classifier Haar Cascade perlu disesuaikan dengan lokasi file pada sistem Anda.
Fungsi add_text dan image_resize bersifat opsional dan tidak digunakan dalam pemrosesan utama.

### Hasil
![image](https://github.com/user-attachments/assets/02df903a-c88e-41f5-ba66-cbe0c56f6622)

## source code
Beberapa baris source kode yang saya ingin bahas

```python
 grayA = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
```
Baris ini mengubah gambar berwarna (frame) menjadi gambar grayscale (skala abu-abu).
Gambar grayscale hanya memiliki satu saluran warna, yaitu intensitas cahaya (luminance).
cv2.cvtColor adalah fungsi dari OpenCV untuk mengubah ruang warna gambar.

```python
    gray = cv2.equalizeHist(grayA)
    face_box = None
    faces = face_cascade.detectMultiScale(gray, 1.1, 3)
```
Baris ini menerapkan teknik equalisasi histogram pada gambar grayscale grayA.
Equalisasi histogram adalah metode untuk meningkatkan kontras suatu gambar dengan mendistribusikan kembali intensitas piksel secara merata.
Hasilnya adalah gambar gray dengan kontras yang lebih baik,


```python
cv2.imshow("Output", frame)
    #cv2.imshow("Output", grayA)
    #cv2.imshow("Output", gray)
```
Codingan di atas untuk menampilkan Output Eye Tracking Video

## Hasil

### Menampilkan Output grayA
![image](https://github.com/user-attachments/assets/107d230d-79f0-41ef-9307-28744559884a)

### Menampilkan Ouput gray
![image](https://github.com/user-attachments/assets/46275c8e-2bcb-4b33-ba0e-ce64959a44db)

