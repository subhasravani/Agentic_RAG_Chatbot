Document Q&A Chatbot using Agentic RAG and MCP
This project is a Retrieval-Augmented Generation (RAG) chatbot designed to answer user questions based on uploaded documents. It uses an agent-based architecture with clearly separated roles and communicates using a custom Model Context Protocol (MCP). The system supports multi-format documents including PDF, DOCX, and TXT files.

Project Highlights
Modular, agent-based system using the principles of autonomy and collaboration between agents.

Ingestion of documents with chunking and vector embedding via FAISS.

Retrieval of top-matching document chunks based on user queries.

Final response generation using Google's Gemini 1.5 Flash large language model.

Integration with Streamlit for a clean and interactive user interface.

Fully executable in Google Colab using LocalTunnel for frontend access.

Architecture
This system is designed with three core agents:

Ingestion Agent
Responsible for processing uploaded documents, splitting them into smaller chunks, and embedding them into a FAISS vectorstore using Google Generative AI Embeddings.

Retrieval Agent
Uses vector similarity search to find the most relevant text chunks in response to a user’s query.

LLM Response Agent
Accepts the retrieved context and the user query, formulates a prompt, and queries Gemini to generate a grounded and contextual answer.

Agents communicate via Model Context Protocol (MCP), which defines standardized messages with sender, receiver, message type, trace ID, and payload.

System Flow
User uploads a document using the UI.

The document is processed by the Ingestion Agent and embedded into a FAISS vectorstore.

When a query is entered, the Retrieval Agent performs a similarity search.

The retrieved chunks are passed to the LLM Response Agent, which uses Gemini to generate the final answer.

The answer is displayed to the user via the Streamlit UI.

Technology Stack
Streamlit for UI

FAISS for vector similarity search

LangChain for managing LLM workflows and document processing

Google Generative AI for embeddings

Gemini 1.5 Flash model for generating responses

Python, Google Colab, LocalTunnel for backend and hosting

Challenges Faced
Compatibility issues with Gemini model names and API versions.

Deserialization errors with FAISS when loading stored indexes.

Managing long document chunks that exceed default token limits.

Streamlit limitations in Google Colab, requiring use of LocalTunnel for web UI access.

Ensuring consistent formatting and chunk quality across different document types.

Future Improvements
Support for multiple file uploads in a single session.

Adding source highlighting to indicate where the answer was extracted from.

Better error handling and UI feedback.

OCR support for scanned or image-based PDFs.

Deployment on HuggingFace Spaces or Streamlit Cloud for broader access.
