# 🧠 PDF QA System with LangChain, OpenAI, and Chroma

This project implements a question-answering (QA) system over PDF documents using the LangChain framework. It uses OpenAI's GPT-3.5 Turbo for reasoning and Chroma as a vector database to retrieve the most relevant document chunks based on user queries.

## 📚 Overview

The application loads a PDF file, splits its content into manageable chunks, stores them in a vector database (Chroma), and enables querying over the data using natural language. When a user submits a question, the system fetches the most relevant chunks and sends them to a language model for a contextualized response.

## 🚀 Features

- PDF document loading and preprocessing
- Text chunking using LangChain’s `RecursiveCharacterTextSplitter`
- Embedding with OpenAI models
- Vector search with Chroma
- Question answering using `gpt-3.5-turbo`
- Serverless-compatible `lambda_handler` for integration with AWS Lambda or other platforms

## 📦 Dependencies

Make sure the following Python packages are installed:

```bash
pip install langchain langchain-openai langchain-community chromadb
```

You'll also need to set your OpenAI API key:

```bash
export OPENAI_API_KEY="your-api-key"
```

## 🧩 Project Structure

- `loadData()`: Loads and splits the PDF into chunks, then stores them in Chroma DB.
- `getRelevantDocs(question)`: Retrieves the most relevant chunks based on a question.
- `ask(question, llm)`: Combines the retrieved chunks with a prompt and asks the LLM for an answer.
- `lambda_handler(event, context)`: AWS Lambda entry point to process JSON-based questions and return responses.

## ⚙️ Example Input

```json
{
  "body": "{\"question\": \"What does the document say about data privacy?\"}"
}
```

## ✅ Example Output

```json
{
  "statusCode": 200,
  "headers": {
    "Content-Type": "application/json"
  },
  "body": {
    "message": "Tarefa Concluída com sucesso",
    "details": "<Generated answer based on context>"
  }
}
```

## 📄 Notes

- The system currently processes a hardcoded PDF: `DOC-SF238339076816-20230503.pdf`. Update the filename in `loadData()` as needed.
- Responses are tailored for legal and technical documents and written in Brazilian Portuguese.

