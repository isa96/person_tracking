# Project 2: Person Tracking (Object Detection)

Proyek ini menampilkan beragam percobaan arsitektur dan algoritma Convolitional Neural Network (CNN) dalam Computer Vision melalui implementasi object detection menggunakan 
dataset COCO2017. Dengan melakukan eksperimen berbagai varian dari algoritma Faster RCNN dan YOLO, model ini dilatih untuk mendeteksi kelas person pada datset COCO2017.

## 🚀 Sorotan Utama:

Teknik    : Menggunakan teknik computer vision dengan library Pytorch dan OpenCV.

Model     : Faster RCNN dengan backbone GoogleNet, MobileNet dan ResNet50. YOLO dengan versi 3,5 dan 8.

Kinerja   : Mencapai prediksi terbaik dengan backbone ResNet50 pada Faster RCNN dan YOLOv8 pada YOLO.

    Jelajahi kode dan hasil untuk mendapatkan wawasan tentang object detection kelas person!

📝 Catatan: Proyek ini merupakan bagian dari Bootcamp Computer Vision oleh Indonesia AI dan dikerjakan secara kolaboratif oleh kelompok CV B -Oppenheimer dan CV D -Alan Turing

## ★ Introduction

### Background

Dalam era perkembangan teknologi komputer dan kecerdasan buatan, pemantauan objek dan deteksi manusia menjadi fokus utama dalam berbagai aplikasi, 
termasuk keamanan lingkungan, pemantauan lalu lintas, sampai dengan sektor industri dan perdagangan. Sistem pelacakan manusia yang efektif menjadi kunci 
untuk meningkatkan keamanan dan efisiensi di berbagai kondisi lingkungan.

### Problem Statement

Dalam deteksi objek khususnya person tracking, terdapat beberapa tantangan dikarenakan perubahan pose dan interaksi antar objek dalam satu frame. 
Eksplorasi algoritma Faster RCNN dan YOLO diharapkan memberikan solusi terkait deteksi manusia yang cepat dan akurat. 
Proyek ini bertujuan mengatasi kendala deteksi dalam kerumunan, perubahan pose, dan pemantauan real-time, mendukung pengembangan sistem pelacakan manusia yang lebih efisien.
  
## ★ Getting Started

### 1. Data collection & Preparation

#### 🔍 Dataset : [COCO (Common Objects in Context)](https://cocodataset.org/#explore)

<img align="left" src="https://cocodataset.org/images/coco-logo.png" alt="Deskripsi Gambar" width="300" height="180">
Dataset diambil dari COCO (Common Objects in Context) menggunakan library Fiftyone. Dataset merupakan kumpulan data gambar yang berisi sekitar 118.287 
gambar pelatihan (train images) dan 5.000 gambar validasi (val images). Setiap gambar di dalam dataset ini memiliki beberapa anotasi objek, 
yang membuat total jumlah anotasi objek lebih dari 860.000. Dalam pemrosesan kami menyaring data sebanyak 5000 gambar dengan class ‘Person’ beserta label 
anotasi gambar yang memuat bounding box pada pixel yang menunjukkan kelas person pada gambar yang diambil. Kemudian melakukan split data menjadi data training sebanyak 4000, 
validation sebanyak 500 dan test sebanyak 500.

### 2. Model Development

### FASTER RCNN :
##### Backbone GoogLeNet:
- Menggunakan GoogleNet (Inception V1) & InceptionV3
- Mengaplikasikan augmentasi Normalization
- Mencoba Optimizer SGD dengan lr = 0.0001, momentum = 0.9, weight decay = 0.0001
- Mencoba Optimizer Adam dengan lr = 0.001
- Menambahkan LR scheduler (gamma=0.1)

##### Backbone MobileNet
- Menggunakan mobilenet_v3_large_fpn & mobilenet_v3_large_320_fpn
- Mengaplikasikan augmentasi Normalization
- Mencoba Optimizer SGD dengan lr = 0.005 dan 0.1, momentum = 0.9, weight decay = 0.0005 dan 0.0001
- Menambahkan LR scheduler (gamma=0.1)

##### Backbone ResNet50
- Menggunakan Resnet50 sebagai pretrained
- Mengaplikasikan augmentasi Normalization
- Mencoba Optimizer SGD dengan lr = 0.005, momentum = 0.9, weight decay = 0.0005
- Menambahkan LR scheduler (gamma=0.1)
 
### YOLO :
##### Versi yang diexplorasi:
- YOLO V3 : YOLO V3u
- YOLO V5 : YOLO V5s, YOLO V5x
- YOLO V8 : YOLOV8m, YOLOV8l, YOLOV8x

##### Hyperparameter yang digunakan:
- Epochs         : 50 dan 100
- Batch          : 8 dan 16
- Image Size     : 640x640
- Learning Rate  : lr0 = 0.01, lrf = 0.0001
- Momentum       : 0.937
- Weight Decay   : 0.0005
- Optimizer      : AdamW  

##### Augmentation yang diaplikasikan:
- Mosaic : 1.0
- Translate: 0.1
- Scale: 0.5
- fliplr: 0.5
- hsv_h (hue): 0.015
- hsv_s (saturation): 0.7
- hsv_v (value): 0.4

### 3. Training & Optimization

Pada tahap ini, dilakukan pelatihan dan optimasi model menggunakan beberapa arsitektur dan algoritma yang berbeda, yaitu Faster RCNN dengan Backbone GoogLeNet, 
MobileNet, ResNet50, dan YOLO dengan versi 3, 5, dan 8. Proses ini dilakukan untuk mencari arsitektur yang memberikan hasil terbaik pada dataset COCO untuk tujuan person detection.

#### * Evaluasi Hasil Training

Setelah pelatihan, model dievaluasi menggunakan dataset validasi untuk mengukur akurasi hasil prediksi. Metric evaluasi yang digunakan adalah Precision, Recall, dan mAP.





