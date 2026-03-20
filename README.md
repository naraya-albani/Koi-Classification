# 🐟 Koi Classification

Proyek machine learning untuk mengklasifikasikan jenis ikan koi berdasarkan gambar menggunakan deep learning. Model dilatih menggunakan TensorFlow/Keras dan diekspor ke berbagai format untuk keperluan deployment di berbagai platform.

---

## 📁 Struktur Proyek

```
Koi-Classification/
├── notebook.ipynb          # Notebook utama: eksplorasi data, pelatihan, dan evaluasi model
├── requirements.txt        # Daftar dependensi Python
├── saved_model/            # Model dalam format TensorFlow SavedModel
├── tfjs_model/             # Model dalam format TensorFlow.js (untuk deployment web)
└── tflite/                 # Model dalam format TensorFlow Lite (untuk deployment mobile/edge)
```

---

## 🧠 Deskripsi Proyek

Proyek ini membangun model klasifikasi gambar untuk mengenali berbagai jenis ikan koi. Pipeline lengkap mencakup:

- **Preprocessing data** — augmentasi dan normalisasi gambar
- **Pelatihan model** — menggunakan arsitektur CNN (Convolutional Neural Network) dengan TensorFlow/Keras
- **Evaluasi model** — metrik akurasi, confusion matrix, dan visualisasi hasil
- **Konversi model** — ekspor ke SavedModel, TensorFlow.js, dan TensorFlow Lite untuk fleksibilitas deployment

---

## ⚙️ Instalasi

### Prasyarat

- Python 3.8+
- pip

### Langkah Instalasi

1. Clone repositori ini:
   ```bash
   git clone https://github.com/naraya-albani/Koi-Classification.git
   cd Koi-Classification
   ```

2. Install dependensi:
   ```bash
   pip install -r requirements.txt
   ```

3. Jalankan notebook:
   ```bash
   jupyter notebook notebook.ipynb
   ```

---

## 🚀 Penggunaan Model

### 1. TensorFlow SavedModel
Cocok untuk deployment menggunakan TensorFlow Serving atau inferensi langsung via Python.

```python
import tensorflow as tf

model = tf.saved_model.load("saved_model/")
# Lakukan inferensi
predictions = model(input_tensor)
```

### 2. TensorFlow.js
Cocok untuk deployment di browser atau aplikasi web berbasis Node.js.

```javascript
import * as tf from '@tensorflow/tfjs';

const model = await tf.loadGraphModel('tfjs_model/model.json');
const prediction = model.predict(inputTensor);
```

### 3. TensorFlow Lite
Cocok untuk deployment di perangkat mobile (Android/iOS) atau edge device.

```python
import tensorflow as tf

interpreter = tf.lite.Interpreter(model_path="tflite/model.tflite")
interpreter.allocate_tensors()

input_details = interpreter.get_input_details()
output_details = interpreter.get_output_details()

interpreter.set_tensor(input_details[0]['index'], input_data)
interpreter.invoke()
output = interpreter.get_tensor(output_details[0]['index'])
```

---

## 📊 Alur Pelatihan

Berikut adalah alur kerja utama yang ada di dalam `notebook.ipynb`:

1. **Persiapan Dataset** — Memuat dan membagi dataset ke dalam set pelatihan, validasi, dan pengujian
2. **Augmentasi Data** — Teknik augmentasi seperti rotasi, flip, dan zoom untuk meningkatkan generalisasi model
3. **Pembangunan Model** — Arsitektur CNN atau transfer learning dengan base model pre-trained
4. **Pelatihan & Validasi** — Melatih model dengan monitoring loss dan akurasi
5. **Evaluasi** — Confusion matrix dan classification report per kelas ikan koi
6. **Konversi & Ekspor** — Model diekspor ke format SavedModel, TFLite, dan TF.js

---

## 🗂️ Format Model yang Tersedia

| Format | Folder | Kegunaan |
|---|---|---|
| TensorFlow SavedModel | `saved_model/` | Server-side inference, TF Serving |
| TensorFlow.js | `tfjs_model/` | Aplikasi web / browser |
| TensorFlow Lite | `tflite/` | Android, iOS, Raspberry Pi |

---

## 🛠️ Teknologi yang Digunakan

- **TensorFlow / Keras** — Framework deep learning utama
- **TensorFlow.js** — Konversi dan deployment di web
- **TensorFlow Lite** — Konversi dan deployment di mobile/edge
- **NumPy & Pandas** — Manipulasi data
- **Matplotlib / Seaborn** — Visualisasi data dan hasil pelatihan
- **Jupyter Notebook** — Lingkungan eksperimen interaktif

---

## 👤 Author

**Naraya Albani**
- GitHub: [@naraya-albani](https://github.com/naraya-albani)

---

## 📄 Lisensi

Proyek ini bersifat open-source. Silakan gunakan dan modifikasi sesuai kebutuhan dengan mencantumkan atribusi yang sesuai.
