# fruitcheck
## 🍎 Deskripsi

FruitCheck adalah sistem klasifikasi kualitas buah menggunakan metode **Kernel Extreme Learning Machine (KELM)** dengan akurasi **99.3%**. Sistem ini dapat mengklasifikasikan 5 jenis buah (Apple, Banana, Grape, Mango, Orange) ke dalam 3 kategori kualitas: Fresh, Formalin-mixed, dan Rotten.

## ✨ Fitur Utama

- 🎯 Akurasi tinggi: 99.3% (mean), 99.7% (best fold)
- 🚀 Prediksi real-time
- 🎨 UI modern dengan TailwindCSS
- 📱 Responsive design
- 🖼️ Drag & drop upload
- 🔍 Support 5 jenis buah

## 🛠️ Teknologi

- **Backend**: Flask (Python)
- **Machine Learning**: KELM (Kernel Extreme Learning Machine)
- **Feature Extraction**: ResNet50
- **Frontend**: HTML5, TailwindCSS, JavaScript
- **Libraries**: scikit-learn, NumPy, Pandas, Pillow

## 📋 Requirement

```bash
Python 3.8+
Flask 3.0.0
NumPy 1.24.3
Pandas 2.0.3
scikit-learn 1.3.0
Pillow 10.0.0
```

## 🚀 Cara Menjalankan

### 1. Install Dependencies

```bash
pip install -r requirements.txt
```

### 2. Pastikan Model Files Ada

Pastikan file-file berikut ada di direktori yang sama dengan `app.py`:

- `kelm_best_model_fold*.pkl` (model KELM)
- `label_encoder.pkl` (label encoder)
- `model_metadata.pkl` (metadata model)

### 3. Jalankan Aplikasi

```bash
python app.py
```

### 4. Buka Browser

Akses aplikasi di: `http://127.0.0.1:5000`

## 📁 Struktur Direktori

```
.
├── app.py                          # Flask application
├── requirements.txt                # Python dependencies
├── README_FLASK.md                 # Documentation
├── templates/
│   └── index.html                  # Landing page
├── uploads/                        # Temporary upload folder
├── kelm_best_model_fold*.pkl      # Trained model
├── label_encoder.pkl               # Label encoder
└── model_metadata.pkl              # Model metadata
```

## 🎯 Cara Menggunakan

1. **Upload Gambar**

   - Klik tombol "Choose File" atau drag & drop gambar
   - Format yang didukung: PNG, JPG, JPEG (Max 16MB)

2. **Tunggu Proses**

   - Sistem akan mengekstrak fitur dari gambar
   - Model KELM akan melakukan prediksi

3. **Lihat Hasil**
   - Hasil klasifikasi akan ditampilkan
   - Kategori: Fresh, Formalin-mixed, atau Rotten

## ⚙️ Parameter Model

- **Algorithm**: KELM (Kernel Extreme Learning Machine)
- **Kernel**: RBF (Radial Basis Function)
- **C**: 100
- **Sigma**: 15
- **Gamma**: 0.002222
- **K-Fold**: 9

## 📊 Performance Metrics

- Mean Accuracy: **99.3%**
- Best Fold Accuracy: **99.7%** (Fold 8)
- Standard Deviation: Low variance
- Classes: 15 (5 fruits × 3 conditions)

## 🍎 Supported Fruits

1. **Apple** (Apel)
2. **Banana** (Pisang)
3. **Grape** (Anggur)
4. **Mango** (Mangga)
5. **Orange** (Jeruk)

## 🏷️ Classification Categories

1. **Fresh**: Buah segar berkualitas tinggi
2. **Formalin-mixed**: Buah terkontaminasi formalin
3. **Rotten**: Buah busuk/tidak layak konsumsi

## ⚠️ Important Notes

### Feature Extraction

File `app.py` saat ini menggunakan **placeholder** untuk ekstraksi fitur. Anda perlu mengganti fungsi `extract_features()` dengan metode yang sama yang digunakan saat training:

```python
def extract_features(image_path):
    # TODO: Ganti dengan metode ekstraksi fitur yang sebenarnya
    # Contoh: ResNet50, VGG16, atau custom CNN

    # Load dan preprocess image
    img = Image.open(image_path).convert('RGB')
    img = img.resize((224, 224))

    # Extract features menggunakan model yang sama saat training
    features = your_feature_extractor.predict(img)

    return features
```

### Model Files

Pastikan model files yang di-load adalah hasil dari notebook training (`klasifikasi_kelm_fruits.ipynb`).

## 🔧 Troubleshooting

### Error: Model not loaded

- Pastikan file model ada di direktori yang benar
- Check nama file: `kelm_best_model_fold*.pkl`

### Error: Feature extraction failed

- Update fungsi `extract_features()` sesuai metode training
- Pastikan dimensi fitur sama dengan saat training

### Error: Port already in use

- Ubah port di `app.py`: `app.run(port=5001)`

## 📝 TODO

- [ ] Implementasi feature extraction yang sebenarnya
- [ ] Tambah confidence score
- [ ] Tambah batch prediction
- [ ] Export hasil ke CSV/Excel
- [ ] Add API documentation

## 👨‍💻 Development

Untuk development mode:

```bash
export FLASK_ENV=development  # Linux/Mac
set FLASK_ENV=development     # Windows
python app.py
```

## 📄 License

MIT License - Free to use for educational and commercial purposes.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📧 Contact

For questions or support, please contact the development team.

---

**Built with ❤️ using KELM & Flask**
