### **Project Title**
**Retrieval Augmented Generation (RAG) and Conversational AI for Multi-Source Document Analysis**

### **Project Overview**
This project addresses the challenge of Large Language Models (LLMs) lacking access to private or real-time data, which often leads to "hallucinations" when queried on specific internal knowledge. I developed a modular RAG pipeline that enables a chatbot to retrieve and synthesize information from diverse datasets—including technical PDFs and Notion databases—rather than relying solely on pre-training data. The implementation utilizes the LangChain framework to orchestrate document loading, vector embeddings, and semantic retrieval, resulting in a conversational interface capable of high-accuracy document-based question answering.

### **Business Understanding**
The primary stakeholders for this project are organizational knowledge managers and data scientists who require tools to query internal documentation efficiently. A significant business problem is the "data silo" effect, where critical information is trapped in unstructured formats like handbooks, transcripts, or meeting notes. By implementing a RAG system, organizations can significantly reduce the time spent on manual information retrieval and avoid the prohibitive costs associated with fine-tuning models on rapidly changing datasets.

### **Data Understanding**
The analysis leveraged a diverse set of unstructured data sources to test the system's flexibility across different formats:
* **Data Sources:** The project utilized technical lecture PDFs (e.g., Stanford CS229), Notion-based corporate repositories (e.g., Blendle’s Employee Handbook), and YouTube video transcripts.
* **Timeframe:** The data includes academic materials and historical company documentation.
* **Data Limitations:** The quality of the output is heavily dependent on the chunking strategy; overly small chunks may lose context, while large chunks may exceed the LLM's context window. Additionally, the system is limited by the semantic accuracy and dimensional density of the vector embeddings used.
* **Exploratory Analysis:** Initial data inspection focused on metadata preservation, ensuring that source attribution (e.g., page numbers or document origin) remained intact for citation purposes in the final chatbot output.

### **Modeling and Evaluation**
The project implemented a multi-stage modeling process designed for semantic precision:
* **Preprocessing:** Documents were processed using the **RecursiveCharacterTextSplitter**, which maintains semantic integrity by creating overlapping text chunks.
* **Vectorization:** I utilized **OpenAIEmbeddings** to transform text into high-dimensional vectors stored in a **Chroma** vector database for efficient similarity searches.
* **Retrieval Algorithm:** The system compared standard similarity searches with **Maximal Marginal Relevance (MMR)** and **SVM-based retrievers** to ensure a balance between relevance and diversity in retrieved results.
* **LLM Integration:** A **ConversationalRetrievalChain** was employed to manage chat history, allowing the model to handle follow-up questions effectively.
* **Evaluation Metrics:** Success was evaluated based on the **Retrieval Precision** (the relevance of the context provided to the LLM) and the **Answer Accuracy** (the degree to which the generated response aligned with the source document).

### **Conclusion**
The system successfully demonstrates that RAG pipelines can transform static document repositories into interactive, queryable assets that provide grounded, fact-based responses. 
* **Recommendations:** To enhance production-level performance, I recommend implementing a **Parent Document Retrieval** strategy to provide the LLM with broader context and a **re-ranking model** to refine retrieval results. 
* **Future Steps:** I intend to expand this project by integrating an automated evaluation framework (such as RAGAS) and exploring open-source LLM alternatives to reduce reliance on proprietary APIs.
