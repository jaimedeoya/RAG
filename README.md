# RAG - Retrieval-Augmented Generation (prueba)

Pequeño proyecto de RAG local con interfaz en Gradio. Permite subir documentos, indexarlos en una base vectorial y hacerles preguntas usando un LLM local.

## ¿Qué hace?

1. **Indexa documentos** — carga archivos PDF, TXT, DOCX o EPUB, los divide en chunks y los guarda en ChromaDB con embeddings de HuggingFace (`all-MiniLM-L6-v2`).
2. **Recupera contexto** — ante una pregunta, busca los chunks más relevantes en la base vectorial.
3. **Genera respuesta** — envía el contexto recuperado a un LLM local vía [LM Studio](https://lmstudio.ai/) (`meta-llama-3.1-8b-instruct`).
4. **Variaciones de consulta** — genera 5 reformulaciones de la pregunta para mejorar la recuperación semántica.

## Stack

| Componente | Tecnología |
|---|---|
| Interfaz | Gradio |
| Embeddings | HuggingFace `sentence-transformers/all-MiniLM-L6-v2` |
| Vector store | ChromaDB |
| LLM | LM Studio (OpenAI-compatible API) |
| Loaders | LangChain (PDF, TXT, DOCX, EPUB) |

## Requisitos

```bash
pip install ebooklib beautifulsoup4 gradio langchain chromadb sentence-transformers pypdf docx2txt
```

LM Studio corriendo en `http://localhost:1234` con un modelo cargado.

## Uso

Ejecutar el notebook `RAg.ipynb` y abrir la interfaz Gradio que se genera.
