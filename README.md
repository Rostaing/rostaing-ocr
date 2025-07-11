## Rostaing OCR, created by Davila Rostaing.

An advanced, pure-Python OCR package for extracting text from PDFs and images. It is specifically designed to **preserve the original document's vertical reading order**, making it ideal for integration into AI applications like LLMs and RAG pipelines.

This tool produces clean plain text (`.txt`) and Markdown (`.md`) files **without requiring any external software installation** like Tesseract.

## Key Features

-   ✨ **Zero External Dependencies**: Unlike wrappers for Tesseract, `rostaing-ocr` is 100% Python. Just `pip install` and you're ready to go.
-   🧠 **Layout-Aware Extraction**: **Preserves the vertical reading order** of documents. Text from a header image will appear before the body text, and a footer will appear last, creating a logically coherent output.
-   🚀 **High-Accuracy Deep Learning OCR**: It delivers excellent results on both scanned and digital documents.
-   📄 **Handles Mixed Content**: Intelligently extracts text from both the text layer of a PDF and the text embedded within images on the same page.
-   ⚙️ **Versatile Input**: Processes single or multiple files (PDFs, PNGs, JPGs, etc.) in a single run.
-   📦 **Flexible Output**: Generates both clean text (`.txt`) and structured Markdown (`.md`) files and can print results directly to the console.

## Installation

### Best Practice: Use a Virtual Environment

To keep project dependencies isolated, using a virtual environment is highly recommended.

**On macOS/Linux:**
```bash
# Create an environment named '.venv'
python3 -m venv .venv

# Activate the environment
source .venv/bin/activate
```

**On Windows:**
```bash
# Create an environment named '.venv'
python -m venv .venv

# Activate the environment
.venv\Scripts\activate
```

## Install the Package
With your virtual environment activated, install the package and its deep learning backend (PyTorch) from PyPI with one simple command:
```bash
# This installs the main library and the PyTorch backend
pip install rostaing-ocr
```

**Note:** The first time you run the extractor, **rostaing-ocr** will automatically download the necessary language models. This may take a moment and requires an internet connection. This is a one-time process.

## Usage
Using the library is designed to be simple. The extraction process starts immediately upon creating an instance of the RostaingOCR class.

## --- Example 1: Simple processing of a single file ---
This creates 'output.md' and 'output.txt' with the extracted content.
```bash
from rostaing_ocr import RostaingOCR

extractor = RostaingOCR(
    "path/to/my_document.pdf", 
    print_to_console=True # Optional: see results in the terminal
    output_basename="combined_report", # Optional: custom name for output files
)

# Print the object to get a summary of the operation.
print(extractor)
```

## --- Example 2: Advanced processing of multiple files ---
This processes two files, customizes the output name, specifies languages, and prints the full content to the console.
```bash
from rostaing_ocr import RostaingOCR

multi_extractor = RostaingOCR(
    input_path_or_paths=["report.pdf", "receipt.jpg"],
    output_basename="combined_report", # Optional: custom name for output files
    print_to_console=True,             # Optional: see results in the terminal
    ocr_lang=['fr', 'en'],             # Optional: specify languages for OCR
    perform_ocr=True                   # Optional: OCR is enabled by default
)

print(multi_extractor)
```

## Application for LLM and RAG Pipelines
Large Language Models (LLMs) like GPT-4 or Llama understand text, not images or scanned documents. A vast amount of valuable knowledge is locked away in unstructured formats such as PDFs of research papers, scanned invoices, or legal contracts.
rostaing-ocr serves as the crucial first step in any data ingestion pipeline for Retrieval-Augmented Generation (RAG) systems. By converting visual data into clean, semantically ordered text, it unlocks this data for LLMs. The layout-aware extraction ensures that the context (e.g., a title appearing before a paragraph) is maintained, leading to better performance in RAG systems.

A typical workflow:

1. Input: A directory of PDFs or Images.
2. Extraction (rostaing-ocr): Convert all documents into clean, logically ordered Markdown/Text.
3. Processing: The text output can be fed into text splitters and then embedding models.
4. Indexing: The resulting vectors are stored in a vector database (e.g., Chroma, Pinecone, FAISS) for efficient retrieval.

In short, rostaing-ocr unlocks your documents, making them ready for any modern AI stack.

## License
This project is licensed under the MIT License. See the LICENSE file for more details.

## Useful Links
- Github: https://github.com/Rostaing/rostaing-ocr
- PyPI: https://pypi.org/project/rostaing-ocr/
- LinkedIn: https://www.linkedin.com/in/davila-rostaing/
- YouTube: [youtube.com/@RostaingAI](https://youtube.com/@rostaingai?si=8wo5H5Xk4i0grNyH)