# Keyword Extraction Experiments

This notebook contains experiments for extracting keywords from academic papers using KeyBERT.

## Setup

```python
# Install required packages
!pip install -q keybert sentence-transformers transformers pdfplumber

# Import libraries
from keybert import KeyBERT
from sentence_transformers import SentenceTransformer
import pdfplumber
import pandas as pd
```

## Load Model

```python
# Initialize KeyBERT with SentenceTransformer
kw_model = KeyBERT(model=SentenceTransformer('all-MiniLM-L6-v2'))
```

## Extract Text from PDF

```python
def extract_text_from_pdf(pdf_path):
    """Extract text from PDF file"""
    text = ""
    with pdfplumber.open(pdf_path) as pdf:
        for page in pdf.pages:
            text += page.extract_text() or ""
    return text

# Example usage
# pdf_path = "../data/sample_papers/sample.pdf"
# text = extract_text_from_pdf(pdf_path)
# print(f"Extracted {len(text)} characters")
```

## Extract Keywords

```python
def extract_keywords(text, top_n=10):
    """Extract top N keywords from text"""
    keywords = kw_model.extract_keywords(
        text,
        keyphrase_ngram_range=(1, 2),
        stop_words='english',
        top_n=top_n,
        use_maxsum=True,
        nr_candidates=20,
        diversity=0.7
    )
    return keywords

# Example usage
# keywords = extract_keywords(text, top_n=10)
# for keyword, score in keywords:
#     print(f"{keyword}: {score:.4f}")
```

## Visualize Results

```python
import matplotlib.pyplot as plt

def visualize_keywords(keywords):
    """Visualize keyword scores"""
    df = pd.DataFrame(keywords, columns=['Keyword', 'Score'])
    
    plt.figure(figsize=(12, 6))
    plt.barh(df['Keyword'], df['Score'])
    plt.xlabel('Relevance Score')
    plt.title('Top Keywords from Document')
    plt.gca().invert_yaxis()
    plt.tight_layout()
    plt.show()

# Example usage
# visualize_keywords(keywords)
```

## Batch Processing

```python
def process_multiple_papers(pdf_paths):
    """Process multiple papers and extract keywords"""
    results = []
    for pdf_path in pdf_paths:
        try:
            text = extract_text_from_pdf(pdf_path)
            keywords = extract_keywords(text, top_n=10)
            results.append({
                'file': pdf_path,
                'keywords': keywords
            })
        except Exception as e:
            print(f"Error processing {pdf_path}: {e}")
    return results

# Example usage
# pdf_files = glob.glob("../data/sample_papers/*.pdf")
# results = process_multiple_papers(pdf_files)
```

## Save Results

```python
def save_results(results, output_file):
    """Save keyword extraction results to JSON"""
    import json
    
    formatted_results = []
    for result in results:
        formatted_results.append({
            'file': result['file'],
            'keywords': [
                {'keyword': kw, 'score': float(score)}
                for kw, score in result['keywords']
            ]
        })
    
    with open(output_file, 'w') as f:
        json.dump(formatted_results, f, indent=2)
    
    print(f"Results saved to {output_file}")

# Example usage
# save_results(results, "../results/keyword_extraction_results.json")
```

## Notes

- Add your experiments and findings here
- Document parameter tuning results
- Compare different models/approaches
- Note any challenges or limitations
