# ML Models - Sistem Manajemen Referensi Akademik

Model machine learning dan notebook penelitian untuk analisis dokumen berbasis NLP.

## 📊 Gambaran Umum

Repository ini berisi penelitian machine learning, eksperimen, dan model yang digunakan dalam Sistem Manajemen Referensi Akademik untuk:
- **Analisis Kemiripan Dokumen** - Menggunakan Sentence Transformers
- **Ekstraksi Kata Kunci** - Menggunakan KeyBERT
- **Peringkasan Teks** - Menggunakan BART
- **Ekstraksi Referensi** - Menggunakan pola NLP kustom

## 🗂️ Struktur Repository

```
ml-models/
├── notebooks/              # Jupyter notebook untuk eksperimen
│   ├── keyword_extraction.ipynb
│   ├── summarization.ipynb
│   ├── similarity_analysis.ipynb
│   └── reference_extraction.ipynb
├── data/                   # Data sampel untuk pengujian
│   └── sample_papers/      # Paper akademik sampel (PDF)
├── models/                 # Model yang sudah dilatih/fine-tuned
│   └── .gitkeep
├── scripts/                # Script Python untuk pelatihan model
│   └── .gitkeep
├── results/                # Hasil eksperimen dan output
│   └── .gitkeep
├── requirements.txt        # Dependensi Python
└── README.md
```

## 🔬 Model yang Digunakan

### 1. **Ekstraksi Kata Kunci** (KeyBERT)
- **Model**: `all-MiniLM-L6-v2`
- **Tujuan**: Mengekstrak kata kunci utama dari dokumen
- **Metode**: BERT embeddings + MaxSum similarity

### 2. **Peringkasan Teks** (BART)
- **Model**: `facebook/bart-large-cnn`
- **Tujuan**: Menghasilkan ringkasan dokumen
- **Metode**: Peringkasan abstraktif

### 3. **Kemiripan Dokumen** (Sentence Transformers)
- **Model**: `all-MiniLM-L6-v2`
- **Tujuan**: Menghitung kemiripan semantik antar dokumen
- **Metode**: Cosine similarity dari sentence embeddings

### 4. **Ekstraksi Referensi** (NLP Kustom)
- **Metode**: Pattern matching dengan regex
- **Strategi**: Notasi kurung, daftar bernomor, gaya Harvard

## 🚀 Panduan Memulai

### Instalasi

```bash
# Buat virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependensi
pip install -r requirements.txt
```

### Menjalankan Notebook

```bash
# Jalankan Jupyter
jupyter notebook

# Atau gunakan Google Colab (direkomendasikan untuk akses GPU)
# Upload notebook ke Google Drive dan buka dengan Colab
```

## 📓 Daftar Notebook

### 1. Ekstraksi Kata Kunci
- **File**: `notebooks/keyword_extraction.ipynb`
- **Deskripsi**: Eksperimen dengan KeyBERT untuk ekstraksi kata kunci
- **Output**: Top N kata kunci dengan skor confidence

### 2. Peringkasan Dokumen
- **File**: `notebooks/summarization.ipynb`
- **Deskripsi**: Peringkasan teks menggunakan BART
- **Output**: Ringkasan singkat dari paper akademik

### 3. Analisis Kemiripan
- **File**: `notebooks/similarity_analysis.ipynb`
- **Deskripsi**: Komputasi kemiripan dokumen
- **Output**: Matriks kemiripan dan visualisasi

### 4. Ekstraksi Referensi
- **File**: `notebooks/reference_extraction.ipynb`
- **Deskripsi**: Ekstraksi referensi dari paper akademik
- **Output**: Daftar referensi terstruktur

## 🔧 Integrasi Model

Model-model ini diintegrasikan ke dalam API backend:
- **Repository**: [reference-backend](https://github.com/CapstoneKeramikBerkahGroup/reference-backend)
- **Implementasi**: `app/services/nlp_service.py`
- **Fungsi Custom**: `app/services/custom_nlp.py`

## 📊 Metrik Performa

| Task | Model | Accuracy/F1 | Kecepatan |
|------|-------|-------------|-----------|
| Ekstraksi Kata Kunci | KeyBERT | N/A | ~0.5s/doc |
| Peringkasan | BART | N/A | ~2s/doc |
| Kemiripan | SentenceTransformer | N/A | ~0.3s/doc |
| Ekstraksi Referensi | Custom NLP | ~85% | ~0.2s/doc |

## 🧪 Eksperimen

Dokumentasikan eksperimen Anda di notebook:
1. Pemilihan dan perbandingan model
2. Tuning hyperparameter
3. Benchmarking performa
4. Analisis error

## 📦 Dependensi

Paket utama (lihat `requirements.txt` untuk daftar lengkap):
- `transformers` - Hugging Face transformers
- `sentence-transformers` - Embedding kalimat
- `keybert` - Ekstraksi kata kunci
- `torch` - PyTorch backend
- `pdfplumber` - Ekstraksi teks PDF
- `scikit-learn` - Utilitas ML

## 👥 Tim

- **ML Engineer**: [Nama Anggota Tim] - Riset dan pengembangan model
- **NLP Engineer**: [Nama Anggota Tim] - Pipeline NLP dan integrasi
- **Full-Stack Developer**: [Nama Anggota Tim] - Integrasi backend

## 📝 Lisensi

Proyek ini merupakan bagian dari proyek capstone akademik.

## 🔗 Repository Terkait

- [Frontend](https://github.com/CapstoneKeramikBerkahGroup/reference-frontend) - Interface web React
- [Backend](https://github.com/CapstoneKeramikBerkahGroup/reference-backend) - FastAPI backend
- [Deployment](https://github.com/CapstoneKeramikBerkahGroup/reference-deployment) - Konfigurasi Docker (opsional)

## 📧 Kontak

Untuk pertanyaan tentang model ML, hubungi [email-anda@example.com]
