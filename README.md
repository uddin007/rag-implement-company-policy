### Objective
The objective of this project is to:
- Address privacy requirements concerning sensitive information.
- Prevent misinformation.
- Provide specialized content not accessible on the Internet.
- Tailor specific behaviors for customer tasks.
- Manage speed and cost effectively.
- Deploy models on private infrastructure to ensure security.

Model can be accessed via chatbot https://snowflectanalytics.shinyapps.io/dbxendpointapp/

### Retrieval Augmented Generation (RAG)
RAG is an effective GenAI technique that enhances model performance by integrating proprietary data (e.g., business-specific documentation) without requiring model fine-tuning. It achieves this by using custom information as context for the LLM, minimizing incorrect information and enabling the LLM to generate outputs tailored to company-specific data, all while preserving the original model structure. RAG has demonstrated particular effectiveness in chatbots and Q&A systems needing current information or domain-specific knowledge.

### Development
Initially, data is prepared (PDF or HTML) by ingesting and processing it for Vector Search index. Using Data Engineering Lakehouse capabilities, documentation pages are split into smaller segments, their embeddings computed, and stored in a Delta Lake table. With the data prepared, the Vector Search Index can handle similarity queries, locating documentation relevant to user inquiries. This setup enables the creation of a langchain model with an enhanced prompt, leveraging the LLama2 70B model specifically for answering complex Databricks queries.

### Data preparation
First, chatbot responses are enabled by ingesting and indexing documentation pages using a Vector Search index. Ensuring high-quality data preparation is crucial for optimal chatbot performance. Lakehouse AI offers advanced solutions to expedite AI and LLM projects, streamlining data ingestion and preparation on a large scale. In this project, data privacy regulations i.e., GDPR, CCPA documentation (PDF) from online resources are used. 
Following are the steps:
- Utilize autoloader to load binary PDFs into our initial table.
- Employ the unstructured library to extract and parse text content from the PDFs.
- Use either llama_index or Langchain to segment the extracted texts into chunks.
- Compute embeddings for these text chunks.
- Save the segmented text chunks along with their embeddings in a Delta Lake table, which is then ready for Vector Search indexing.

### Embedding model
As embedding model, databricks-bge-large-en is used. BAAI general embedding (BGE) can map any text to a low-dimensional dense vector which can be used for tasks like retrieval, classification, clustering, or semantic search. And it also can be used in vector databases for LLMs.




