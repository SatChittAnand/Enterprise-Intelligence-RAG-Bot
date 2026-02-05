# Enterprise Intelligence RAG Chatbot

A secure, context-aware chatbot capable of answering questions strictly based on uploaded documents. This application utilizes **Retrieval Augmented Generation (RAG)** to provide accurate answers with citations, leveraging Google's Gemini API for embeddings and content generation.

## 🚀 Features

*   **Multi-Format Support**: Upload and analyze PDF, DOCX, and TXT files.
*   **Client-Side Processing**: Document parsing happens in the browser using `pdf.js` and `mammoth.js`.
*   **Strict RAG Mode**: The AI is instructed to answer *only* based on provided context, reducing hallucinations.
*   **Source Citations**: Every answer includes references to the specific document and page number used.
*   **Audit Trail & Reasoning**: View the step-by-step logic, similarity scores, and retrieved context chunks for every response.
*   **Visual Relevance Graph**: Interactive UI showing cosine similarity scores for retrieved data.
*   **Vector Search**: Custom in-memory vector store using Cosine Similarity.

## 🛠️ Tech Stack

*   **Frontend**: React 19, Tailwind CSS
*   **AI Models**:
    *   *Embeddings*: `text-embedding-004`
*   **SDK**: `@google/genai`
*   **Document Parsing**: `pdf.js`, `mammoth`

## ⚙️ Architecture

1.  **Ingestion**: Files are uploaded and text is extracted in the browser.
2.  **Chunking**: Text is split into sliding window chunks (500 characters with 100 overlap).
3.  **Embedding**: Chunks are sent to the Gemini API (`text-embedding-004`) to generate vector embeddings.
4.  **Storage**: Vectors and metadata are stored in an in-memory Vector Store.
5.  **Retrieval**: User queries are embedded and compared against the store using Cosine Similarity.
6.  **Generation**: Top 5 relevant chunks are sent as context to `gemini-2.5-flash` to generate the final answer.


## 🏃‍♂️ How to Run

1.  **Clone the repository**.
2.  **Install dependencies** (if running in a local Node environment):
    ```bash
    npm install
    ```
3.  **Set your API Key**:
    *   If using a local bundler (Vite/Webpack), create a `.env` file:
        ```
        REACT_APP_API_KEY=your_api_key_here
        ```
        *Note: The current codebase uses `process.env.API_KEY`. Ensure your bundler exposes this.*

4.  **Start the application**:
    ```bash
    npm start
    ```

## 📖 Usage Guide

1.  **Upload Documents**: Click the "+" button in the sidebar or drag and drop PDF/DOCX/TXT files.
2.  **Wait for Processing**: The app will parse text and generate embeddings (indicated by a spinner).
3.  **Ask Questions**: Type your query in the chat input.
4.  **Review Answers**:
    *   Check **Sources** at the bottom of the response to see where information came from.
    *   Click **View Reasoning** to see the retrieval scores and the exact text chunks passed to the LLM.

## 🛡️ Privacy Note

While document parsing happens locally in the browser, text chunks are sent to the Google Gemini API to generate embeddings and final responses. Ensure you comply with your organization's data privacy policies regarding third-party API usage.

## 📄 License

[MIT Licence](https://github.com/SatChittAnand/Enterprise-Intelligence-RAG-Bot/blob/main/LICENSE)



View app: https://ai.studio/apps/drive/1VHQ1XqodxGZO66v_SZU5FjsWoVQioCM7

view graph: https://robert-mcdermott.github.io/ai-knowledge-graph/

Agile Document: https://docs.google.com/spreadsheets/d/1A1p7p5yNqVytPq37rgL-rBBQJfWGE1Nc56P3_M39_Bo/edit?usp=sharing


