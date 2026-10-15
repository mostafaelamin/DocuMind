# DocuMind — AI-Powered Document Assistant

**Developed by Mostafa Elamin**

DocuMind is a Python application that lets users upload PDF documents, ask questions about their contents, and receive AI-generated answers with page references. It runs **Llama 3.2 locally through Ollama**, without requiring a paid AI API.

## Features

- **PDF text extraction:** Reads text-based PDFs using PyMuPDF.
- **Document Q&A:** Answers questions based on extracted PDF text using Llama 3.2.
- **Conversational chat:** Keeps recent messages in the active Streamlit session for follow-up questions.
- **Page references:** Requests citations in the format `[Page 2]` and includes a page-by-page source text viewer.
- **Document dashboard:** Shows page count, word count, and file size.
- **Custom interface:** A dark-themed Streamlit workspace with DocuMind branding.
- **Local inference:** Uses Ollama on the user's own computer.

## Tech Stack

- **Python** — application logic
- **Streamlit** — web interface
- **PyMuPDF** — PDF text extraction
- **Ollama** — local model runtime
- **Llama 3.2** — language model

## Getting Started

### Prerequisites

- Python 3.12 or later
- [Ollama](https://ollama.com/) installed and running
- Git (to clone the repository)

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/mostafaelamin/DocuMind.git
   cd DocuMind
   ```

2. Create and activate a virtual environment:

   **macOS / Linux**
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

   **Windows (PowerShell)**
   ```powershell
   py -m venv .venv
   .venv\Scripts\Activate.ps1
   ```

3. Install the Python dependencies:

   ```bash
   python -m pip install -r requirements.txt
   ```

4. Download the local model:

   ```bash
   ollama pull llama3.2
   ```

5. Ensure Ollama is running, then launch DocuMind:

   ```bash
   python -m streamlit run app.py
   ```

6. Open **http://localhost:8501** if it doesn't open automatically.

## How It Works

1. Upload a text-based PDF in the sidebar.
2. PyMuPDF extracts the document's text and labels it by page.
3. DocuMind sends up to the first 10,000 characters of extracted text, along with recent chat messages, to the local Llama 3.2 model.
4. The model generates an answer and is prompted to include page references.
5. Use the source text viewer to check the referenced pages.

## Limitations

- Only the **first 10,000 characters** of the document are sent to the model; later content may not be available for answers.
- Page citations are **AI-generated, not automatically verified**. Check important claims against the source.
- Scanned or image-only PDFs without extractable text are not supported.
- Chat history is held in Streamlit session state and is not saved permanently.
- Running the app requires Ollama and the Llama 3.2 model on the local machine. Publishing the source code to GitHub does not host a live version of the app.

## Future Improvements

- Retrieval-augmented generation (RAG) for large PDFs
- Semantic search with embeddings
- Multiple-document analysis
- Persistent conversation history
- Programmatic citation verification

## Developer

**Mostafa Elamin**  
GitHub: [@mostafaelamin](https://github.com/mostafaelamin)

Built to explore Python development, generative AI, and local document intelligence.
