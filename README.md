# Facial-Emotion-Music-Recommender
Sistem AI untuk merekomendasikan playlist musik berdasarkan ekspresi wajah. Menggunakan CNN dengan dataset FER-2013 untuk mendeteksi 6 emosi wajah dan memetakan ke genre musik yang sesuai.

## Deskripsi Proyek

Proyek ini adalah sistem rekomendasi musik berbasis Kecerdasan Buatan yang menganalisis ekspresi wajah seseorang untuk menyarankan playlist musik yang sesuai dengan mood. Menggunakan model Convolutional Neural Network (CNN), sistem ini dilatih untuk mengidentifikasi 6 emosi dasar: **marah (Angry), takut (Fear), bahagia (Happy), netral (Neutral), sedih (Sad), dan terkejut (Suprise - sesuai dataset)**.

Dataset FER-2013 digunakan untuk melatih model, dan teknik `class_weight` diterapkan untuk mengatasi masalah ketidakseimbangan kelas dalam dataset. Setelah emosi terdeteksi dari gambar yang diunggah, sistem akan merekomendasikan lagu-lagu yang telah dikurasi untuk mood tersebut, memberikan pengalaman personal yang unik kepada pengguna.

## Fitur Utama

* **Deteksi Ekspresi Wajah Akurat:** Menggunakan model CNN yang dilatih khusus untuk mengklasifikasikan ekspresi wajah dari gambar.
* **Identifikasi 6 Emosi:** Mampu mendeteksi dan mengkategorikan emosi ke dalam 'Angry', 'Fear', 'Happy', 'Neutral', 'Sad', dan 'Suprise'.
* **Rekomendasi Musik Persona:** Menawarkan rekomendasi playlist musik yang dipetakan secara manual, disesuaikan dengan mood yang terdeteksi.
* **Antarmuka Interaktif:** Memungkinkan pengguna mengunggah gambar wajah langsung melalui Google Colab untuk analisis dan rekomendasi instan.
* **Penanganan Ketidakseimbangan Data:** Mengimplementasikan `class_weight` selama pelatihan untuk mengurangi bias model terhadap kelas yang dominan.

## Teknologi yang Digunakan

* **Python 3.x**
* **TensorFlow & Keras:** Framework utama untuk Deep Learning.
* **NumPy:** Untuk komputasi numerik.
* **Matplotlib:** Untuk visualisasi data dan grafik.
* **`sklearn.utils.class_weight`:** Untuk menangani ketidakseimbangan kelas.
* **Google Colab:** Sebagai lingkungan pengembangan berbasis Jupyter Notebook.

## Cara Menjalankan Proyek (di Google Colab)

1.  **Akses Google Colab:** Buka [colab.research.google.com](https://colab.research.google.com/).
2.  **Unggah Notebook:** Klik `File -> Upload notebook` dan unggah file `facial_emotion_music_recommender.ipynb` ini ke Colab.
3.  **Siapkan Dataset:**
    * Unduh dataset FER-2013 (yang berisi folder `Training` dan `Testing` dengan gambar-gambar ekspresi wajah) dalam format `.zip`. Pastikan Anda mendapatkan versi yang berisi folder `Training/Training/` dan `Testing/Testing/` jika itu yang sesuai dengan notebook Anda.
    * Unggah file `.zip` tersebut ke Google Drive Anda (misalnya, di `My Drive/Datasets/dataset.zip`).
    * **Sesuaikan `PATH_TO_YOUR_ZIP`** di **Sel 2** pada notebook (`/content/drive/MyDrive/Datasets/dataset.zip`) agar menunjuk ke lokasi file `.zip` Anda di Google Drive.
4.  **Jalankan Sel Kode:**
    * Jalankan setiap sel kode secara berurutan, dari **Sel 1 hingga Sel 7**.
    * **Sel 1 & 2:** Mengimpor library, menghubungkan Google Drive, dan mengekstrak dataset.
    * **Sel 3:** Pra-pemrosesan data dengan `ImageDataGenerator`. Pastikan `NUM_CLASSES` disetel ke `6` sesuai dengan deteksi aktual dari dataset Anda.
    * **Sel 3a (sel baru setelah Sel 3):** Menghitung `class_weights`.
    * **Sel 4:** Membangun arsitektur model CNN.
    * **Sel 5:** Melatih model dengan `class_weight`. Proses ini akan memakan waktu.
    * **Sel 6:** Mengevaluasi model dan menyiapkan fungsi prediksi.
    * **Sel 7:** Sistem rekomendasi musik interaktif. Jalankan sel ini dan unggah gambar wajah Anda untuk mendapatkan rekomendasi!

## Informasi Dataset

Proyek ini menggunakan dataset **FER-2013 (Facial Expression Recognition Dataset)**.
* Dataset ini terdiri dari gambar wajah *grayscale* berukuran 48x48 piksel.
* Meskipun aslinya memiliki 7 kelas, versi dataset yang digunakan di sini terdeteksi memiliki **6 kelas emosi**: 'Angry', 'Fear', 'Happy', 'Neutral', 'Sad', dan 'Suprise'.
* Dataset ini seringkali memiliki masalah ketidakseimbangan kelas, yang telah diatasi dengan implementasi `class_weight`.

## Kinerja Model

Model CNN dilatih selama 100+ *epoch* dengan implementasi `class_weight` untuk mengatasi ketidakseimbangan data. Hasilnya menunjukkan peningkatan akurasi yang signifikan:

**Akurasi Model pada Data Pengujian Akhir: Sekitar 61.71%**

Angka ini menunjukkan bahwa model memiliki kemampuan yang baik dalam mengklasifikasikan ekspresi wajah.

### Grafik Hasil Pelatihan Model:

Berikut adalah visualisasi dari performa model selama pelatihan (akurasi dan loss):
![grafikepoch](https://github.com/user-attachments/assets/51763ead-f2e2-46a6-b13d-cbd996ffbd01)


## Dokumentasi Hasil dan Contoh Penggunaan

Berikut adalah contoh penggunaan sistem rekomendasi musik ini dengan gambar wajah yang diunggah:

![Screenshot 2025-07-10 144731](https://github.com/user-attachments/assets/e5da6de7-6dc8-4f28-9360-93d862fee134)


## Peningkatan di Masa Depan

* **Peningkatan Akurasi Model:** Eksplorasi arsitektur CNN yang lebih kompleks, penyesuaian hyperparameter (misalnya *learning rate*), atau penggunaan teknik *transfer learning* dari model yang sudah terlatih (misalnya VGG16, ResNet).
* **Integrasi API Musik:** Menghubungkan sistem dengan API layanan musik populer (seperti Spotify atau YouTube Data API) untuk rekomendasi lagu secara real-time dan memainkan cuplikan lagu.
* **Deteksi Wajah Real-time:** Mengimplementasikan deteksi ekspresi wajah dari video kamera (membutuhkan lingkungan lokal yang lebih *powerful*).
* **Ekstraksi Fitur Audio:** Menganalisis fitur audio lagu secara otomatis untuk mengelompokkan dan merekomendasikan musik yang lebih akurat berdasarkan karakteristik suara.
* **Perbaikan Dataset:** Mencari atau membuat dataset yang lebih seimbang dan berkualitas tinggi, atau menerapkan teknik *oversampling* yang lebih canggih.

## Kontributor

* **[Nama Lengkap Anda]** ([Profil GitHub Anda](https://github.com/your-username)) - Mahasiswa Informatika [Semester Anda Saat Ini]

## Lisensi

Proyek ini dilisensikan di bawah Lisensi MIT. Lihat file [LICENSE](LICENSE) untuk detailnya.

---
