# Vibe-Matcher
“Vibe Matcher” — a fashion recommendation mini-system where the input query (vibe) is matched against a small product catalog using OpenAI embeddings + cosine similarity, falling back to TF-IDF if the API quota is exhausted.

## Why AI at Nexora
Artificial Intelligence fascinates me because of its ability to merge creativity with logic — transforming raw data into intelligent, personalized experiences. Nexora’s focus on building human-centered, innovative AI systems aligns perfectly with my passion for developing models that feel intuitive, useful, and impactful. I’m excited by how Nexora combines research-grade intelligence with real-world applications, and I see this as the ideal place to grow technically while contributing to meaningful AI-driven projects.

---

## Project Overview
This project is a **mini recommendation system** that matches user “vibes” to fashion products using **vector similarity**.  
Given a natural-language query (e.g., *“energetic urban chic”*), the system finds the top-3 most semantically similar products from a mock fashion catalog.

---

## Features
✅ Uses **OpenAI text embeddings (`text-embedding-ada-002`)** for semantic similarity  
✅ Falls back to **TF-IDF cosine similarity** when API quota is exceeded  
✅ Automatically **caches embeddings** to prevent redundant API calls  
✅ **Evaluates latency and match quality** for multiple test queries  
✅ Includes **visual plots** for latency and score distribution  
✅ Ends with a clear **reflection** section (metrics, improvements, edge cases)

---

## Tech Stack
| Category | Tools / Libraries |
|-----------|-------------------|
| Language | Python 3.x |
| AI / Embeddings | OpenAI API (`text-embedding-ada-002`) |
| Vector Search | Cosine Similarity (`scikit-learn`) |
| Fallback | TF-IDF Vectorizer |
| Data Handling | Pandas, NumPy |
| Visualization | Matplotlib |

---

## Project Structure

vibe-matcher/
├── vibe_matcher_notebook.ipynb # Main Notebook (Colab/Jupyter)
├── requirements.txt # Dependencies
├── embeddings_cache.pkl # Cached embeddings (auto-created)
├── latency_by_query.png # Latency visualization
├── score_distribution.png # Similarity histogram
└── README.md # Project documentation

---

## How to Run
1. **Clone this repo**
   ```bash
   git clone https://github.com/yourusername/vibe-matcher.git
   cd vibe-matcher

2. Install dependencies
   pip install -r requirements.txt

3. Set your OpenAI API key
   export OPENAI_API_KEY="your_api_key_here"

4. Run the notebook
   - Open vibe_matcher_notebook.ipynb on Colab or Jupyter
   - Execute cells sequentially
   - If the OpenAI quota is exceeded, the notebook automatically switches to TF-IDF mode.

---

## Reflection

What went well:

  - Simple, explainable pipeline: vibe text → embeddings → cosine similarity → top-3.
  - Reliability-first design: caching, retries, and TF-IDF fallback ensure robustness.
  - Consistent scoring across both OpenAI and TF-IDF modes.

Edge cases handled:

  - No/weak matches trigger fallback recommendations.
  - API limit → automatic switch to TF-IDF space.
  - Caching reduces redundant API calls and speeds reruns.

Next steps / Improvements:

  - Integrate Pinecone or FAISS for large-scale vector databases.
  - Combine similarity with product popularity or price-based ranking.
  - Add precision@k and MRR metrics for quantitative evaluation.
