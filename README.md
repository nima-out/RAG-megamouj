# RAGUdemy

A hands-on learning project for building the main components of a
**Retrieval-Augmented Generation (RAG)** pipeline with Python, LangChain,
Hugging Face embeddings, ChromaDB, and Ollama.

The notebooks progress from loading and chunking different data sources to
creating embeddings, performing semantic search, persisting vectors, and
connecting retrieval results to a local language model. English and Persian
examples are included.

## What this project covers

- Loading plain-text files and entire directories
- Parsing PDF and Microsoft Word documents
- Converting CSV, Excel, and SQLite data into LangChain documents
- Cleaning text and comparing chunking strategies
- Generating local embeddings with
  `sentence-transformers/all-MiniLM-L6-v2`
- Measuring cosine similarity and implementing basic semantic search
- Storing and retrieving vectors with a persistent ChromaDB collection
- Building a simple RAG chain with LangChain and a local Ollama model
- Retrieving and answering questions in Persian as well as English

## Project structure

```text
RAGUdemy/
|-- 0-DataIngestion/
|   |-- 1-dataingestion.ipynb          # Text loading and chunking
|   |-- 2-dataparsingpdf.ipynb         # PDF loading, cleaning, and chunking
|   |-- 03-dataparsingdoc.ipynb        # Word document loaders
|   |-- 04-csvexcelparsing.ipynb       # Basic structured-data example
|   |-- 6-databaseparsing.ipynb        # SQLite data to documents
|   `-- data/                           # Sample TXT, PDF, DOCX, CSV, and DB files
|-- 1-VectorEmbeddingsAndDatabases/
|   `-- emvedding.ipynb                # Embeddings and semantic similarity
|-- 2-VectorStores/
|   |-- 01-chromadb.ipynb              # ChromaDB retrieval and a RAG chain
|   `-- chroma_db/                      # Example persistent Chroma collection
|-- main.py                             # Minimal Python entry point
|-- pyproject-dependency.toml           # Project metadata and dependencies
`-- uv.lock                             # Locked dependency versions
```

## Prerequisites

- [Python 3.13](https://www.python.org/downloads/)
- [uv](https://docs.astral.sh/uv/getting-started/installation/) for environment
  and dependency management
- [Ollama](https://ollama.com/) only for the final local-LLM example
- Git and a Jupyter-compatible editor, such as JupyterLab or VS Code

The embedding notebook downloads its Hugging Face model the first time it is
run, so an internet connection is required for that initial download.

## Installation

Clone the repository and enter its directory:

```bash
git clone https://github.com/<your-username>/RAGUdemy.git
cd RAGUdemy
```

The dependency manifest is currently named `pyproject-dependency.toml`. Copy it
to the standard name expected by `uv`:

```bash
# macOS or Linux
cp pyproject-dependency.toml pyproject.toml

# Windows PowerShell
Copy-Item pyproject-dependency.toml pyproject.toml
```

Create the environment and install the locked dependencies:

```bash
uv sync
```

## Running the notebooks

Start JupyterLab from the project root:

```bash
uv run jupyter lab
```

Then open the notebooks in this suggested order:

1. `0-DataIngestion/1-dataingestion.ipynb`
2. `0-DataIngestion/2-dataparsingpdf.ipynb`
3. `0-DataIngestion/03-dataparsingdoc.ipynb`
4. `0-DataIngestion/04-csvexcelparsing.ipynb`
5. `0-DataIngestion/6-databaseparsing.ipynb`
6. `1-VectorEmbeddingsAndDatabases/emvedding.ipynb`
7. `2-VectorStores/01-chromadb.ipynb`

You can also verify the basic Python entry point with:

```bash
uv run python main.py
```

## Using the Ollama RAG example

The final section of `2-VectorStores/01-chromadb.ipynb` expects Ollama to be
available at `http://127.0.0.1:11434`.

1. Install and start Ollama.
2. Pull a model supported by your machine.
3. Replace the notebook's `model` value with the exact name returned by
   `ollama list`.
4. Run the ChromaDB and RAG-chain cells in order.

The included prompt asks the model to produce a short answer in Persian using
only the retrieved context.

## Notes

- Notebook paths are relative to their working directories. If your editor
  starts kernels from the repository root, update paths such as `data/...` to
  `0-DataIngestion/data/...`.
- `emvedding.ipynb` contains an example absolute Windows path. Replace it with
  the path to `0-DataIngestion/data/word_files/cmd_report.docx` on your system.
- The first PDF-loader examples reference `data/pdf/attention.pdf`; the sample
  currently included in the repository is `data/pdf/32.pdf`.
- Running the ChromaDB notebook can update the files inside
  `2-VectorStores/chroma_db/`.
- This repository is educational and the notebooks are intended to be run cell
  by cell.

## Core technologies

- [LangChain](https://python.langchain.com/)
- [ChromaDB](https://www.trychroma.com/)
- [Hugging Face Sentence Transformers](https://www.sbert.net/)
- [Ollama](https://ollama.com/)
- [pandas](https://pandas.pydata.org/)
- [Jupyter](https://jupyter.org/)

## Contributing

Issues, corrections, and learning examples are welcome. Fork the repository,
create a focused branch, and open a pull request describing your change.

## License

No license has been added yet. Add a license file before redistributing or
reusing the project outside the terms allowed by copyright law.
