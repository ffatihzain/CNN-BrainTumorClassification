# 🧠 Deteksi Tumor Otak dengan CNN

## Tujuan Pembelajaran
Memahami konsep implementasi Convolutional Neural Network (CNN) untuk deteksi tumor otak menggunakan citra MRI (Magnetic Resonance Imaging).

## Deskripsi Proyek
Proyek ini mengimplementasikan sistem deteksi tumor otak otomatis menggunakan deep learning dengan arsitektur CNN. Sistem dapat mengklasifikasikan citra MRI otak menjadi dua kategori:

- Tumor Detected: Citra mengandung tumor otak
- No Tumor: Citra normal tanpa tumor

## Dataset
- Sumber: Brain MRI Images for Brain - Tumor Detection (Kaggle)
- Total Gambar: 253 citra MRI otak (155 dengan tumor, 98 tanpa tumor)
- Format: Gambar RGB
- Kategori: 2 kelas (Tumor/No Tumor)
- Resolusi: Dinormalisasi ke 224x224 piksel

## Teknologi yang Digunakan
**Framework & Library**
- TensorFlow/Keras: Framework deep learning untuk membangun model CNN
- PIL (Python Imaging Library): Manipulasi dan loading gambar
- NumPy: Operasi array dan matriks numerik
- Matplotlib: Visualisasi data dan hasil prediksi
- OpenCV (cv2): Library computer vision untuk preprocessing gambar
- Scikit-learn: Pembagian dataset untuk training dan testing

**Komponen Deep Learning**
- Convolutional Neural Network (CNN): Arsitektur neural network untuk analisis citra medis
- Binary Classification: Klasifikasi dua kelas (tumor/no tumor)
- Data Normalization: Standarisasi nilai piksel ke rentang 0-1

### 📂 Struktur Alur Kerja
1. **Persiapan Dataset**
    - Dataset MRI otak diunduh dari Kaggle menggunakan KaggleHub
    - Gambar diorganisir dalam folder "yes" (tumor) dan "no" (non-tumor)
    - Setiap gambar MRI diproses ke ukuran 224x224 piksel dan dikonversi ke RGB
    - Normalisasi nilai piksel dengan membagi 255.0 (rentang 0-1)

2. **Eksplorasi dan Visualisasi Data**
    - Menampilkan contoh gambar dari kedua kategori untuk pemahaman visual
    - Menghitung distribusi kelas: 155 gambar dengan tumor dan 98 gambar tanpa tumor
    - Verifikasi dimensi gambar input (224x224x3)

3. **Pemberian Label dan Pembagian Data**
    - Gambar tumor diberi label 1, gambar non-tumor diberi label 0
    - Dataset dibagi dengan rasio 80% training dan 20% testing
    10% data training dipisahkan untuk validasi selama proses training

4. **Arsitektur Model CNN**

| Library | 	Konfigurasi | Output Shape | Parameter # |
|---------|--------------|--------------|--------------|
| **Conv2D** | 32 filter (3x3), ReLU, valid padding | (222, 222, 32)| 896 |
| **MaxPooling2D** | Pool size (2x2) | (111, 111, 32) | 0
| **Flatten** | - | (394272) | 0
| **Dense** | 256 neuron, ReLU | (256) | 100933888 |
| **Dropout** | Rate 0.5 | (256) |0
| **Dense (Output)** | 1 neuron, sigmoid | (1) | 257 |


5. **Training Model**
- Optimizer: Adam
- Loss Function: Binary Cross-Entropy
- Metric: Accuracy
- Batch Size: 32
- Epochs: 10
- Validasi: Dataset validasi digunakan untuk monitoring performa

6.  **Evaluasi Model**
- Visualisasi kurva akurasi dan loss pada data training dan validasi
- Evaluasi final pada dataset testing
- Model disimpan dalam format HDF5 untuk penggunaan masa depan

## 📝 Kesimpulan

Proyek Deteksi Tumor Otak dengan CNN ini mendemonstrasikan aplikasi praktis dari deep learning dalam bidang radiologi medis. Sistem berhasil mengklasifikasikan citra MRI otak dengan akurasi yang menjanjikan, menunjukkan potensi AI untuk membantu profesional medis dalam diagnosis tumor otak.

### Aplikasi Klinis
- **Alat Bantu Diagnostik**: Membantu radiolog dan dokter dalam screening awal citra MRI otak
- **Deteksi Dini***: Mendukung identifikasi tumor otak pada tahap awal saat peluang pengobatan masih tinggi
- **Efisiensi Waktu**: Mempercepat proses diagnosis dengan otomatisasi screening awal

### Potensi Implementasi
- **Telemedicine**: Dapat diintegrasikan dengan sistem telemedicine untuk daerah terpencil
- **Screening Massal**: Berpotensi untuk program screening massal dengan biaya rendah
- **Sistem Pendukung Keputusan**: Dapat berfungsi sebagai second opinion dalam sistem pendukung keputusan klinis

### Pengembangan Lanjutan
- Rotasi, flipping, dan scaling untuk memperkaya dataset
- Penambahan layer konvolusi untuk ekstraksi fitur yang lebih kaya
- Visualisasi feature maps untuk interpretasi model
- Klasifikasi multi-kelas untuk berbagai jenis tumor
