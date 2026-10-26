# 🧠 RAG with n8n — Build a Knowledge Pipeline & RAG AI Agent

**From Documents → Embeddings → Vector Database → Retrieval → AI Agent → Grounded Answer**

---

## 📌 1. Project Overview

RAG with n8n is a practical implementation of a **Retrieval-Augmented Generation (RAG)** system using n8n, Supabase Vector Store, Gemini, and OpenAI Embeddings.

The project demonstrates how to build a knowledge-based AI system that processes documents, stores their content as searchable vector embeddings, retrieves relevant information, and uses an AI Agent to generate answers grounded in the retrieved knowledge.

Unlike a ready-made RAG interface, this project exposes the main components and workflows to demonstrate how the system works.

🎯 **The goal is to understand RAG as a complete system architecture, not simply as an AI node or feature.**

## 🚨 2. Business Problem

AI models do not automatically have access to an organization's private documents, internal knowledge, or changing domain-specific information.

Relying only on a language model can lead to:

- ❌ Answers that are not supported by the available documents.
- 🔍 Difficulty finding specific information in large files.
- 📄 Retrieving entire documents when only a small section is relevant.
- ⚠️ Hallucinations when the required information is unavailable.
- 🔗 Limited control over the relationship between retrieved information and generated answers.
- 🧩 Difficulty understanding and debugging the individual components of a RAG system.

## 💡 3. Proposed Solution

The project builds a RAG system with two connected workflows:

- 📥 **Knowledge Ingestion Pipeline:** Processes documents and prepares them for retrieval.
- 🤖 **RAG AI Agent:** Receives user questions, searches the knowledge base, and generates answers using retrieved information.

The system:

- 📂 Detects files added to a Google Drive folder.
- ⬇️ Downloads files and extracts their text.
- ✂️ Splits documents into smaller chunks.
- 🔢 Converts chunks into embeddings.
- 💾 Stores document content, metadata, and embeddings in Supabase.
- 💬 Receives user questions through the n8n Chat Trigger.
- 🔎 Searches for relevant information through a Vector Store Tool.
- 🧠 Uses Gemini to interpret retrieved information and generate answers.
- 💭 Uses Simple Memory to maintain conversation context.
- 🛡️ Instructs the Agent not to invent unsupported information.
- 🧪 Tests retrieval quality, unknown questions, and conversation memory.

## 🎯 4. Project Objectives

- 🧠 Understand the complete RAG architecture.
- 📄 Learn how documents are loaded and processed.
- ✂️ Understand chunking and chunk overlap.
- 🔢 Understand embeddings and semantic similarity search.
- 💾 Configure Supabase as a vector database.
- 🔗 Connect n8n workflows with Supabase.
- 🤖 Build an AI Agent that uses a knowledge base as a tool.
- 💬 Distinguish conversational memory from external knowledge.
- 🔍 Distinguish retrieval from answer generation.
- 🧪 Test system behavior and diagnose failures.
- 🛡️ Reduce unsupported answers through grounding instructions and testing.
- 🏗️ Understand when RAG is appropriate for a real AI solution.

## 🛠️ 5. Technology Stack

| **Technology** | **Purpose** |
|---|---|
| 🔄 n8n | Workflow automation and AI orchestration |
| ☁️ Google Drive | Stores source documents and triggers ingestion |
| 🗄️ Supabase | Stores document chunks and vector embeddings |
| 🐘 PostgreSQL | Database underlying the Supabase vector store |
| 🔎 pgvector | Supports vector storage and similarity search |
| 🤖 Google Gemini | Understands questions and generates answers |
| 🔢 OpenAI Embeddings | Converts documents and questions into vectors |
| ✂️ Recursive Character Text Splitter | Divides documents into manageable chunks |
| 📄 Default Data Loader | Converts extracted content into document objects |
| 🧠 Simple Memory | Maintains conversational context |
| 💬 n8n Chat Trigger | Receives user questions |

**Embedding model used in the documented setup:** `text-embedding-3-small`

**Important:** The embedding model and the Supabase vector column dimensions must be compatible.

## 🔗 6. System Architecture

The system consists of two main workflows: preparing the knowledge base and using that knowledge to answer questions.

### 🏗️ Complete Architecture

```text
                🧠 RAG SYSTEM
                      |
          +-----------+-----------+
          |                       |
          v                       v
  📥 KNOWLEDGE PIPELINE     🤖 RAG AI AGENT
          |                       |
     Google Drive              User Question
          |                       |
     Download File           Chat Trigger
          |                       |
     Extract Text               AI Agent
          |                  /     |     \
     Load Document       Gemini  Memory  Vector Tool
          |                                |
       Chunking                         Embeddings
          |                                |
      Embeddings                            v
          |                         Supabase Search
          v                                |
  Supabase Vector Store             Relevant Chunks
                                           |
                                           v
                                     Gemini / LLM
                                           |
                                           v
                                     Grounded Answer
```

### 🧩 Component Responsibilities

- 📂 **Google Drive Trigger:** Detects relevant file changes in the selected folder.
- ⬇️ **Google Drive Download:** Downloads the actual file.
- 📝 **Extract From File:** Extracts text from the PDF.
- 📄 **Default Data Loader:** Converts extracted text into document objects.
- ✂️ **Recursive Character Text Splitter:** Divides documents into smaller chunks.
- 🔢 **OpenAI Embeddings:** Generates vector representations of document chunks and questions.
- 💾 **Supabase Vector Store:** Stores and retrieves document chunks.
- 💬 **Chat Trigger:** Receives user questions.
- 🤖 **AI Agent:** Determines how to use the available tools to answer a question.
- 🧠 **Gemini Chat Model:** Interprets retrieved context and generates the response.
- 💭 **Simple Memory:** Maintains conversation context.
- 🔎 **Vector Store Tool:** Enables the Agent to search the knowledge base.

⚠️ **Important:** The Knowledge Ingestion Pipeline is a workflow, not an AI Agent. The RAG AI Agent is responsible for interacting with users and using the knowledge base.

## 📥 7. Knowledge Ingestion Pipeline

The first workflow transforms source documents into searchable knowledge.

### 🔄 Workflow Sequence

```text
Google Drive Trigger
        |
        v
Edit Fields — File ID
        |
        v
Google Drive Download
        |
        v
Extract From File
        |
        v
Default Data Loader
        |
        v
Recursive Character Text Splitter
        |
        v
OpenAI Embeddings
        |
        v
Supabase Vector Store
```

### ⚙️ Main Configuration

**1. Google Drive Trigger**

- Select the folder containing the knowledge documents.
- Configure the trigger to monitor relevant file changes.
- Use an appropriate schedule supported by your n8n version.

**2. Edit Fields**

Extract the file ID from the trigger output.

The file ID and file name can also be retained as metadata to identify the original source of each chunk.

**3. Google Drive Download**

Use the file ID to download the actual document as binary data.

**4. Extract From File**

Extract the text from the PDF before passing it to the document-processing components.

**5. Default Data Loader**

Convert the extracted content into document objects containing:

- `pageContent`: The text content.
- `metadata`: Additional information about the source.

**6. Recursive Character Text Splitter**

Split the document into smaller chunks.

Example starting configuration:

| **Setting** | **Example Value** |
|---|---:|
| Chunk Size | 500 |
| Chunk Overlap | 50 |

These are starting values for experimentation, not universal optimal settings.

**7. OpenAI Embeddings**

Use `text-embedding-3-small` to generate vector representations of the chunks.

**8. Supabase Vector Store**

Insert the processed documents, embeddings, and metadata into the database.

## 🗄️ 8. Supabase Vector Database Configuration

The project uses **Supabase + PostgreSQL + pgvector** to store and retrieve vector embeddings.

### 📋 Database Requirements

The documented setup uses a `documents` table with the following fields:

| **Field** | **Purpose** |
|---|---|
| `id` | Identifies the stored record |
| `content` | Stores the chunk text |
| `metadata` | Stores additional source information |
| `embedding` | Stores the vector representation |

Example metadata:

```json
{
  "file_id": "123",
  "file_name": "RAG.pdf"
}
```

### ⚙️ Configuration Steps

1. Create a Supabase project.
2. Enable the `vector` extension if it is not already enabled.
3. Use the Supabase SQL Editor and the documented LangChain Quick Start to create the required vector-store structure.
4. Confirm that the `documents` table exists.
5. Confirm that the `match_documents` function exists when using the corresponding Quick Start setup.
6. Configure the Supabase credentials in n8n.
7. Ensure the embedding dimensions match the selected embedding model.

### 🔎 Why Do We Need `match_documents`?

The function enables similarity search by finding document chunks relevant to a query vector.

The documented configuration uses:

- **Table Name:** `documents`
- **Query Name:** `match_documents`

These names must match the actual database objects.

🔐 **Security:** Store credentials in n8n credentials. Never publish API keys, Supabase secret keys, or service-role keys in GitHub or project documentation.

## 🤖 9. RAG AI Agent

The second workflow allows users to ask questions and receive answers based on the stored knowledge.

### 🔄 Workflow Sequence

```text
User Question
      |
      v
Chat Trigger
      |
      v
AI Agent
  /    |    \
 v     v     v
Gemini Memory Vector Store Tool
                  |
                  v
          OpenAI Embeddings
                  |
                  v
         Supabase Vector Store
                  |
                  v
          Relevant Chunks
                  |
                  v
              AI Agent
                  |
                  v
               Gemini
                  |
                  v
                Answer
```

### 🧩 Agent Components

**1. Chat Trigger**

Receives the user's question and passes it to the AI Agent.

**2. Google Gemini Chat Model**

Processes the question, interprets the retrieved information, and generates the answer.

Gemini is the language model, not the knowledge base.

**3. Simple Memory**

Maintains context between messages in a conversation.

For example:

- User: What is RAG?
- Agent: RAG retrieves relevant knowledge before generating an answer.
- User: Why is it useful?

Memory helps the Agent understand that “it” refers to RAG.

**4. Supabase Vector Store Tool**

Configure the Vector Store for retrieval as a tool for the AI Agent.

Example configuration:

| **Setting** | **Value** |
|---|---|
| Tool Name | `search_course_knowledge_base` |
| Operation | Retrieve Documents (As Tool for AI Agent), or the equivalent available operation |
| Tool Description | `Search the course knowledge base to retrieve relevant information for answering questions about the course.` |
| Initial Retrieval Limit | 4 |
| Embedding Model | `text-embedding-3-small` |

The retrieval limit is a starting point. It should be adjusted according to testing results.

### 🔢 Why Are Embeddings Used Twice?

**During ingestion:**

```text
Document Chunk
      |
      v
Embedding
      |
      v
Supabase Vector Store
```

**During retrieval:**

```text
User Question
      |
      v
Question Embedding
      |
      v
Similarity Search
      |
      v
Relevant Chunks
```

The system compares the question vector with the stored document vectors to find semantically relevant content.

## 🧠 10. Important RAG Concepts

### 📚 RAG vs Memory

| **Memory** | **RAG** |
|---|---|
| Maintains conversation context | Retrieves external knowledge |
| Remembers relevant previous messages | Searches stored documents |
| Helps understand follow-up questions | Helps answer domain-specific questions |
| Represents conversational context | Represents the knowledge base |

**Memory asks:** What were we discussing?

**RAG asks:** What does our knowledge base say?

### 🔎 Retrieval vs Generation

| **Retrieval** | **Generation** |
|---|---|
| Finds relevant information | Creates the answer |
| Uses embeddings and vector search | Uses the language model |
| Returns relevant document chunks | Combines the question with retrieved context |

### 🗂️ Content vs Metadata

- **Content:** The actual information contained in a document chunk.
- **Metadata:** Information about that content, such as file ID, file name, source, page, or category.

### ✂️ Why Do We Need Chunking?

Chunking divides a large document into smaller, more manageable sections so the system can retrieve relevant information instead of returning an entire document.

There is no single ideal chunk size for every situation. The best configuration depends on the document structure, question types, context size, and retrieval quality.

### 🧭 When Should We Use RAG?

RAG is useful when an AI solution needs to answer questions using private, domain-specific, changing, or external knowledge.

**The goal is not to use RAG simply because we learned it. The goal is to determine whether RAG is the right architecture for the problem.**

## 🧪 11. Testing Plan

The RAG system must be tested systematically. A successful workflow execution does not automatically prove that retrieval and answers are correct.

| **ID** | **Test Scenario** | **Expected Result** |
|---|---|---|
| T01 | 📄 Upload a valid PDF | The ingestion workflow processes the file |
| T02 | 💾 Verify Supabase records | Document chunks and embeddings are stored |
| T03 | ❓ Ask a known question, such as “What is RAG?” | The system retrieves relevant information and answers correctly |
| T04 | 🔎 Ask a semantically similar question using different wording | The system retrieves the relevant information despite wording differences |
| T05 | 🚫 Ask about information absent from the knowledge base | The Agent clearly states that the available knowledge is insufficient |
| T06 | 💭 Ask a follow-up question | Memory helps preserve the conversation context |
| T07 | 🔢 Change the retrieval limit | Retrieval quality is evaluated across configurations |
| T08 | ✂️ Change chunk size or overlap | The effect on retrieval quality is evaluated |
| T09 | ⚙️ Use an incorrect table or query name | The failure is identified and diagnosed |
| T10 | 🔢 Use incompatible embedding dimensions | The configuration issue is identified |
| T11 | 🛡️ Review unsupported claims | The Agent avoids presenting unsupported information as fact |

### 🔬 Additional Validation Checks

- Verify that retrieved chunks actually support the answer.
- Check whether important information is missing from the response.
- Test whether the answer follows the requested format.
- Confirm that the Agent uses the knowledge tool when the question requires it.
- Verify that simple greetings do not require unnecessary knowledge retrieval.
- Test how the system behaves when required information cannot be found.
- Compare retrieval settings without changing multiple variables simultaneously.

### 📸 Testing Evidence

For each executed test, record:

- 🆔 Test ID.
- 💬 Input question or file.
- 🎯 Expected result.
- 🤖 Actual response or workflow output.
- 🔎 Retrieved chunks, where applicable.
- 📋 Pass/Fail status.
- 🐛 Error description and resolution, if needed.

**Testing Status:** Results must be documented after actual execution. A test should not be marked as passed until its expected behavior has been verified.

## ⚠️ 12. Error Handling and Debugging

Debug the system by identifying the layer where the failure occurs rather than assuming the entire workflow is broken.

| **Problem** | **What to Check** |
|---|---|
| ❌ No records in Supabase | Google Drive Trigger, Download, Extract, Data Loader, Splitter, Embeddings, and Vector Store |
| 🔎 Vector search fails | Table name, query function name, and Supabase credentials |
| 🔢 Embedding dimension error | Embedding model and vector column dimensions |
| 🤖 Agent generates unsupported information | System Instructions, Tool Description, and retrieved chunks |
| 📉 Poor retrieval quality | Chunk Size, Chunk Overlap, and retrieval limit |
| 💬 Follow-up question is misunderstood | Simple Memory configuration and conversation context |
| 🔐 Credential-related failure | Credential configuration and access permissions |

### 🛠️ Debugging Workflow

1. Identify the exact failing node or component.
2. Inspect its input and output.
3. Verify the relevant configuration.
4. Identify the likely root cause.
5. Change one variable at a time.
6. Run the relevant test again.
7. Record the outcome.

## 🔐 13. Security and Data Protection

The system connects external services and stores potentially private document content.

Recommended safeguards include:

- 🔑 Store API keys and Supabase credentials securely in n8n credentials.
- 🚫 Never commit secrets or service-role keys to GitHub.
- 🔒 Apply appropriate access controls to the Supabase project.
- 📄 Consider document permissions before ingesting private files.
- 🛡️ Test instructions and retrieved content for potential prompt-injection risks.
- 🔎 Do not treat retrieved document content as trusted system instructions.
- 📋 Avoid exposing unnecessary sensitive information in logs.
- ⚙️ Use only the permissions required by each workflow component.

## 📦 14. Project Deliverables

The project documentation and implementation should include:

- ⚙️ **Knowledge Ingestion Workflow:** Google Drive to Supabase vector storage.
- 🤖 **RAG AI Agent Workflow:** Chat Trigger, AI Agent, Gemini, Memory, and Vector Store Tool.
- 🗄️ **Supabase Configuration:** Required table, vector storage, and retrieval function.
- 🧠 **System Instructions:** Rules for knowledge retrieval and unsupported questions.
- 🧪 **Testing Results:** Evidence from known, semantic, unknown, and follow-up questions.
- 🐛 **Debugging Notes:** Identified issues, root causes, and fixes.
- 📄 **README Documentation:** Architecture, setup, components, and testing.
- 🔐 **Credential Guidance:** Instructions for configuring credentials without publishing secrets.

## 🏆 15. Success Criteria

The project meets its learning objectives when the system can:

- 📥 Process a document through the ingestion pipeline.
- ✂️ Split extracted text into appropriate chunks.
- 🔢 Generate embeddings using the selected model.
- 💾 Store and retrieve document chunks in Supabase.
- 🔎 Find relevant information for a user question.
- 🤖 Use a Vector Store Tool through the AI Agent.
- 💬 Generate answers grounded in retrieved content.
- 🚫 Acknowledge when the knowledge base does not contain enough information.
- 💭 Maintain relevant conversational context.
- 🧪 Demonstrate expected behavior through documented tests.
- 🛠️ Diagnose common configuration and retrieval failures.
- 🔐 Keep credentials outside the published workflow documentation.

## 🎓 16. Key Learning Outcomes

This project demonstrates practical understanding of:

- 🧠 Retrieval-Augmented Generation (RAG).
- ⚙️ Workflow automation using n8n.
- 📄 Document extraction and data loading.
- ✂️ Chunking and chunk overlap.
- 🔢 Embeddings and semantic similarity search.
- 🗄️ Supabase Vector Store and pgvector.
- 🔎 Vector retrieval and query embeddings.
- 🤖 AI Agent and tool integration.
- 💭 Conversational memory and session context.
- 🧪 Systematic testing and debugging.
- 🛡️ Grounded answers and unsupported-information handling.
- 🏗️ Architecture selection and system-layer responsibilities.

## 🚀 Conclusion

RAG with n8n demonstrates how to build a knowledge-based AI solution by connecting document processing, embeddings, vector storage, retrieval, and language-model generation.

The project also demonstrates why each component has a separate responsibility:

- 📥 **Trigger:** Starts the process.
- 📄 **Loader:** Prepares document content.
- ✂️ **Splitter:** Divides content into useful chunks.
- 🔢 **Embeddings:** Represent text numerically.
- 💾 **Vector Store:** Stores and retrieves knowledge.
- 💭 **Memory:** Maintains conversation context.
- 🤖 **AI Agent:** Determines how to use available tools.
- 🧠 **LLM:** Interprets context and generates the response.

### 💡 Final Engineering Principle

**RAG is not a node. RAG is a system architecture.**

A Vector Database does not generate answers. A language model does not automatically know the contents of private documents. An Agent does not replace the knowledge base, and Memory does not replace RAG.

The final engineering question is:

> If I need to build an AI solution for a real business, do I actually need RAG?

The answer depends on the problem, the required knowledge, the constraints, and the risks. The goal is to choose the architecture that fits the real need—not to use a technology simply because it is available.

