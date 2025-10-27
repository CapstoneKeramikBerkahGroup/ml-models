# ML Models - Academic Reference Management System

Machine learning models and research notebooks for NLP-powered document analysis.

## 📊 Overview

This repository contains the machine learning research, experiments, and models used in the Academic Reference Management System for:
- **Document Similarity Analysis** - Using Sentence Transformers
- **Keyword Extraction** - Using KeyBERT
- **Text Summarization** - Using BART
- **Reference Extraction** - Using custom NLP patterns

## 🗂️ Repository Structure

```
ml-models/
├── notebooks/              # Jupyter notebooks for experiments
│   ├── keyword_extraction.ipynb
│   ├── summarization.ipynb
│   ├── similarity_analysis.ipynb
│   └── reference_extraction.ipynb
├── data/                   # Sample data for testing
│   └── sample_papers/      # Sample academic papers (PDF)
├── models/                 # Trained/fine-tuned models
│   └── .gitkeep
├── scripts/                # Python scripts for model training
│   └── .gitkeep
├── results/                # Experiment results and outputs
│   └── .gitkeep
├── requirements.txt        # Python dependencies
└── README.md
```

## 🔬 Models Used

### 1. **Keyword Extraction** (KeyBERT)
- **Model**: `all-MiniLM-L6-v2`
- **Purpose**: Extract top keywords from documents
- **Method**: BERT embeddings + MaxSum similarity

### 2. **Text Summarization** (BART)
- **Model**: `facebook/bart-large-cnn`
- **Purpose**: Generate document summaries
- **Method**: Abstractive summarization

### 3. **Document Similarity** (Sentence Transformers)
- **Model**: `all-MiniLM-L6-v2`
- **Purpose**: Compute semantic similarity between documents
- **Method**: Cosine similarity of sentence embeddings

### 4. **Reference Extraction** (Custom NLP)
- **Method**: Pattern matching with regex
- **Strategies**: Bracket notation, numbered lists, Harvard style

## 🚀 Quick Start

### Installation

```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Running Notebooks

```bash
# Start Jupyter
jupyter notebook

# Or use Google Colab (recommended for GPU access)
# Upload notebooks to Google Drive and open with Colab
```

## 📓 Notebooks

### 1. Keyword Extraction
- **File**: `notebooks/keyword_extraction.ipynb`
- **Description**: Experiments with KeyBERT for keyword extraction
- **Output**: Top N keywords with confidence scores

### 2. Document Summarization
- **File**: `notebooks/summarization.ipynb`
- **Description**: Text summarization using BART
- **Output**: Concise summaries of academic papers

### 3. Similarity Analysis
- **File**: `notebooks/similarity_analysis.ipynb`
- **Description**: Document similarity computation
- **Output**: Similarity matrix and visualization

### 4. Reference Extraction
- **File**: `notebooks/reference_extraction.ipynb`
- **Description**: Extract references from academic papers
- **Output**: Structured list of references

## 🔧 Model Integration

These models are integrated into the backend API:
- **Repository**: [reference-backend](https://github.com/CapstoneKeramikBerkahGroup/reference-backend)
- **Implementation**: `app/services/nlp_service.py`
- **Custom Functions**: `app/services/custom_nlp.py`

## 📊 Performance Metrics

| Task | Model | Accuracy/F1 | Speed |
|------|-------|-------------|-------|
| Keyword Extraction | KeyBERT | N/A | ~0.5s/doc |
| Summarization | BART | N/A | ~2s/doc |
| Similarity | SentenceTransformer | N/A | ~0.3s/doc |
| Reference Extraction | Custom NLP | ~85% | ~0.2s/doc |

## 🧪 Experiments

Document your experiments in the notebooks:
1. Model selection and comparison
2. Hyperparameter tuning
3. Performance benchmarking
4. Error analysis

## 📦 Dependencies

Main packages (see `requirements.txt` for full list):
- `transformers` - Hugging Face transformers
- `sentence-transformers` - Sentence embeddings
- `keybert` - Keyword extraction
- `torch` - PyTorch backend
- `pdfplumber` - PDF text extraction
- `scikit-learn` - ML utilities

## 👥 Team

- **ML Engineer**: [Team Member Name] - Model research and development
- **NLP Engineer**: [Team Member Name] - NLP pipeline and integration
- **Full-Stack Developer**: [Team Member Name] - Backend integration

## 📝 License

This project is part of an academic capstone project.

## 🔗 Related Repositories

- [Frontend](https://github.com/CapstoneKeramikBerkahGroup/reference-frontend) - React web interface
- [Backend](https://github.com/CapstoneKeramikBerkahGroup/reference-backend) - FastAPI backend
- [Deployment](https://github.com/CapstoneKeramikBerkahGroup/reference-deployment) - Docker configs (optional)

## 📧 Contact

For questions about the ML models, contact [your-email@example.com]
