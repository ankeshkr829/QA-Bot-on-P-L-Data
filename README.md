# QA-Bot-on-P-L-Data

Key Components
Python Libraries:

PyPDF2: Extracts text from PDF files.

pandas: For data manipulation (though not explicitly used in this code).

sentence-transformers: Generates embeddings for text data.

faiss: Efficient similarity search for retrieving relevant data.

numpy: Handles numerical operations.

google.generativeai: Integrates with the Gemini API for generating responses.

Steps in the RAG Model:

Step 1: Extract P&L Data from PDF:

The extract_pdf_data function reads a PDF file and extracts text from all pages.

Step 2: Preprocess Data:

The preprocess_data function converts the extracted text into key-value pairs (assumes the text is structured with key: value format).

Step 3: Generate Embeddings and Store in FAISS:

The create_faiss_index function generates embeddings for keys and values using a pre-trained sentence transformer model (all-MiniLM-L6-v2).

These embeddings are stored in a FAISS index for efficient similarity search.

Step 4: Retrieve Relevant Data:

The retrieve_data function encodes the user query, searches the FAISS index, and retrieves the top-k most relevant key-value pairs.

Step 5: Generate Response Using Gemini API:

The generate_response function uses the Gemini API to generate a response based on the retrieved context and the user query.

Example Usage:

The script demonstrates how to use the RAG model to answer financial questions based on a sample PDF (SampleFinancial.pdf).

It retrieves relevant data and generates a response using the Gemini API.

Interactive QA Bot Interface:

The script includes a Streamlit app for an interactive interface.

Users can upload a PDF, ask questions, and receive answers along with the relevant data used to generate the response. 

##Code Improvements and Suggestions
Error Handling:

Add error handling for file operations (e.g., invalid PDF format).

Handle cases where the PDF text extraction fails or returns incomplete data.

Customizable Preprocessing:

The preprocessing step assumes a specific structure (key: value). If the PDF has a different format, the preprocessing logic may need to be adjusted.

FAISS Index Optimization:

Consider using more advanced FAISS index types (e.g., IndexIVFFlat) for larger datasets to improve search efficiency.

Gemini API Key Management:

Avoid hardcoding the API key. Use environment variables or a configuration file for better security.

Streamlit App Enhancements:

Add a progress bar or loading indicator while processing the PDF and generating responses.

Allow users to download the generated response or relevant data as a file.

Testing with Different PDFs:

Test the script with various PDF formats to ensure robustness.

# Financial QA Bot

A Retrieval-Augmented Generation (RAG) model for answering financial questions based on Profit & Loss (P&L) data extracted from PDFs.

## Features
- Extract text from PDF files.
- Preprocess data into key-value pairs.
- Generate embeddings and store them in a FAISS index for efficient retrieval.
- Retrieve relevant data based on user queries.
- Generate responses using the Gemini API.
- Interactive Streamlit app for easy usage.

## Requirements
- Python 3.8+
- Required libraries: `PyPDF2`, `pandas`, `sentence-transformers`, `faiss`, `numpy`, `google-generativeai`, `streamlit`
