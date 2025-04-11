# 🍴 Recipe Chatbot: Your AI-Powered Culinary Assistant

![image](https://github.com/user-attachments/assets/1bc0ac4d-236d-4cfb-8771-583c426fbfa7)


The **Recipe Chatbot** is an advanced AI-powered tool developed in **Google Colab** to assist users in the kitchen. Whether you're looking for recipes, ingredient substitutions, or tips on cooking techniques, this chatbot provides instant, accurate, and context-aware answers. It uses cutting-edge technologies like **Retrieval-Augmented Generation (RAG)**, **HuggingFace models**, **Groq APIs**, and **large language models (LLMs)** to deliver an interactive and seamless experience.

---

## 📋 Key Features

- **Recipe Suggestions**: Based on ingredients, preferences, or user queries.
- **Ingredient Substitutions**: Offers alternatives for unavailable ingredients.
- **Cooking Tips**: Provides guidance on various culinary techniques and methods.
- **Custom Measurement Conversions**: Automatically converts units (e.g., ounces to grams, Fahrenheit to Celsius).
- **Interactive Chat Interface**: User-friendly interface for engaging conversations with the chatbot.
- **Data Organization**: Recipes are categorized for quick and efficient retrieval.

---

## 🛠️ Technologies Used

### Development Environment
- **Google Colab**: Used for scripting, testing, and prototyping the chatbot functionalities.

### Data Extraction and Preparation
- **PyPDF2 & PyMuPDF**: Extract recipe data and related text from PDF files.
- **JSON Conversion**: Extracted data is converted into structured **JSON** format.
- **FAISS**: Vector database for efficient semantic search.
- **LangChain**: Conversational workflow orchestration.

### Conversational AI
- **HuggingFace Models**:
  - Embeddings: `sentence-transformers/all-MiniLM-l6-v2`
  - LLMs: Mistral-7B via Groq API
- **Groq APIs**: Real-time LLM responses
- **LangChain Memory**: Maintains conversation history

### Deployment and Interface
- **Streamlit**: Interactive web interface
- **Localtunnel**: Secure public URL for chatbot access

---

## 🚀 Getting Started

### Prerequisites

- Python 3.7 or higher
- Installed dependencies: `PyPDF2`, `pymupdf`, `gradio`, `faiss-cpu`, `langchain`

### Installation

#### Clone the Repository:
```bash
git clone <repository-url>
cd recipe-chatbot
```

### Install Dependencies:
```bash
pip install -r requirements.txt
```

### Prepare the Data:

- Upload the recipe book PDF to `/content` in Google Colab.
- Adjust the path in the script if needed.

### Extract and Convert Recipes:
```python
from google.colab import files
uploaded = files.upload()

import fitz
def extract_text_from_pdf(file_path):
    doc = fitz.open(file_path)
    text = ''.join(page.get_text() for page in doc)
    return text

import json
with open("recipe_book_data.json", "w") as file:
    json.dump(data, file, indent=4)
```

### Build the FAISS Vector Store:
```python
from langchain.vectorstores import FAISS
vector_db = FAISS.from_documents(documents, embeddings)
vector_db.save_local("/content/faiss_index")
```

---

## 🧠 Setup

Create your chatbot app in `rag_app.py` and run:

```bash
streamlit run rag_app.py & npx localtunnel --port 8501
```

---

## 🌟 Example Interaction

**User Input**:  
> _"What can I make with tomatoes and basil?"_

**Chatbot Response**:
```yaml
🍅 Recipe Name: Tomato Basil Pasta  
🧂 Ingredients: Tomatoes, Basil, Garlic, Olive Oil, Pasta  
👨‍🍳 Instructions: Cook pasta, sauté garlic and tomatoes, stir in basil, combine and serve.
```

---

## ❤️ Credits

Developed with love by **Neringa Pannem**  
Powered by: **LangChain**, **HuggingFace**, **Groq**, **FAISS**, and **Streamlit**



