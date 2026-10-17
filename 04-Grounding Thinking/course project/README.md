# 🖥️ TECHFIX — AI Computer Troubleshooting Assistant

*Turning Technical Knowledge into Practical Guidance.*

## 1. 📌 Project Name

**TECHFIX — AI Computer Troubleshooting Assistant**

An Arabic AI assistant that helps users understand common computer problems and find clear, safe, knowledge-based troubleshooting guidance.

## 2. 🎯 Problem

### 🌐 Context
Many users face computer problems but struggle to understand their possible causes or find clear technical instructions in Arabic.

### ⚠️ Problem
Technical information can be difficult to understand, and general AI answers may include information that is not supported by reliable sources.

### 💡 Why It Matters
Users need clear, relevant, and safe guidance to understand computer problems and identify suitable first steps.

## 3. 💡 Solution

TECHFIX is an Arabic AI assistant built with **Dify**. It uses a specialized knowledge base to retrieve relevant technical information and generate answers based on the available knowledge.

The assistant provides initial troubleshooting guidance, asks for more details when needed, and explains when its knowledge is insufficient.

## 4. 👥 Users

- 💻 Users experiencing common computer problems.
- 🌐 People who need simple technical guidance in Arabic.
- 🔍 Users who want to understand possible causes before contacting a technician.

## 5. 🧩 How I Designed the Solution

I organized the project around four main knowledge areas:

- 🐢 **Computer Performance:** Understanding slow computer problems.
- 💾 **Storage Space:** Understanding storage problems and possible solutions.
- 📶 **Internet Connection:** Troubleshooting Wi-Fi and internet problems.
- 🛡️ **Safety and Limitations:** Providing safe guidance and identifying situations that require a professional technician.

Each topic has a dedicated knowledge document to organize information and support relevant retrieval.

The design also considers retrieval quality, answer accuracy, completeness, and safety.

## 6. ⚙️ How It Works

TECHFIX follows a simple AI workflow:

1. 💬 **User Question:** The user describes a computer problem.
2. 🔎 **Knowledge Retrieval:** Dify searches the knowledge base for relevant information.
3. 🤖 **LLM:** The language model uses the question, instructions, and retrieved information to generate an answer.
4. ✅ **Final Answer:** The assistant provides troubleshooting guidance or explains when more information is needed.

The quality of the final answer depends on the knowledge sources, retrieved results, available context, and how the model uses the information.

## 7. 🤖 Role of AI

AI helps TECHFIX turn retrieved technical information into clear Arabic guidance.

The assistant is instructed to:

- 📚 Use available knowledge to support its answers.
- 🚫 Avoid unsupported claims and troubleshooting steps.
- ❓ Ask for more details when necessary.
- ⚠️ Explain when the available knowledge is insufficient.
- 🛡️ Follow safety instructions.
- 👨‍🔧 Recommend professional help when a problem exceeds its scope.

**Important:** TECHFIX provides guidance only. It does not directly inspect the user's computer or perform repairs.

## 8. 🔄 Automation

TECHFIX uses an AI workflow to connect the user's question, knowledge retrieval, language model, and final answer.

Dify manages the flow between these components, automating information retrieval and answer generation.

This workflow helps users access relevant technical knowledge without manually searching through multiple documents.

## 9. 📂 Data

The knowledge base contains four Markdown documents:

- 🐢 `01-بطء-الحاسوب.md` — Slow computer problems.
- 💾 `02-مساحة-التخزين.md` — Storage space problems.
- 📶 `03-اتصال-الإنترنت.md` — Internet connection problems.
- 🛡️ `04-السلامة-وحدود-المساعدة.md` — Safety rules and assistance limitations.

The documents cover possible causes, initial troubleshooting steps, important conditions, and safety warnings.

The system uses **Retrieval-Augmented Generation (RAG)** to retrieve relevant knowledge before generating an answer.

Knowledge coverage and retrieval quality must be evaluated separately from final answer quality.

## 10. 🛠️ Tools & Technologies

- 🧠 **Dify:** Building and managing the AI application.
- 📚 **Knowledge Base:** Storing organized technical information.
- 🔎 **RAG:** Connecting answer generation with retrieved knowledge.
- 🔍 **Knowledge Retrieval:** Finding information related to user questions.
- 🤖 **Large Language Model (LLM):** Generating natural-language answers.
- 🔄 **Chatflow:** Organizing the workflow between components.
- 📝 **System Prompt:** Defining the assistant's role, behavior, and limitations.
- 📄 **Markdown:** Writing knowledge documents and project documentation.
- 🐙 **GitHub:** Organizing and documenting project files.

## 11. 🎨 Key Design Decisions

- 🌐 Use Arabic to make technical guidance easier to understand.
- 📂 Divide the knowledge base into four specialized documents.
- 🎯 Focus the first version on common computer problems.
- 📚 Use retrieved knowledge to support generated answers.
- ❓ Ask for additional details when a problem description is incomplete.
- 🚫 Avoid unsupported answers when the available knowledge is insufficient.
- 🔍 Evaluate retrieval quality and answer quality separately.
- 🛡️ Make the assistant's limitations and safety rules clear.

## 12. 🧪 Testing

Initial tests covered slow computer performance, storage problems, internet connectivity, and questions involving safety and the assistant's limitations.

The initial results showed that TECHFIX could provide useful guidance in some cases, but answer quality was not consistent across all scenarios.

For example, an answer about an internet connection problem was limited, even though the system retrieved results from the related knowledge document.

This showed that **retrieving relevant information does not guarantee a complete final answer.**

### 🔬 Testing Scenarios

- ✅ **Direct Questions:** Testing questions covered by the knowledge base.
- 🔄 **Paraphrased Questions:** Testing different ways of describing the same problem.
- 📭 **Missing Knowledge:** Checking how the assistant responds when information is unavailable.
- ❓ **Incomplete Questions:** Testing whether the assistant asks for necessary details.
- 🚧 **Out-of-Scope Questions:** Checking whether the assistant respects its scope.
- 🛡️ **Safety-Related Questions:** Evaluating warnings and safe troubleshooting behavior.

### 📊 Evaluation Criteria

- **Relevance:** Are the retrieved results related to the question?
- **Correctness:** Are the provided facts and steps correct?
- **Groundedness:** Are the answer's claims supported by the retrieved information?
- **Completeness:** Does the answer cover the user's problem sufficiently?
- **Clarity:** Are the instructions clear and well organized?
- **Safety:** Does the answer avoid unsafe guidance?
- **Uncertainty Handling:** Does the assistant handle missing information appropriately?

These tests are preliminary and do not represent a complete performance evaluation.

## 13. 📸 Evidence

The project repository is organized to include screenshots documenting the actual implementation.

Planned evidence includes:

- 🖥️ Assistant setup.
- 📚 Knowledge base configuration.
- ⚙️ Retrieval settings.
- 💬 Final answers and testing results.

Screenshots will be added after they are captured from the actual Dify application.

## 14. ⚠️ Challenges & Failures

One observed challenge was that the assistant sometimes generated answers that were too limited, even when relevant information had been retrieved.

This highlighted the difference between **retrieval quality** and **answer quality**.

Possible causes include:

- 📂 Missing or unclear knowledge.
- 🔎 Irrelevant or insufficient retrieved content.
- 🧩 Limited context provided to the model.
- 📝 Instructions that do not guide answer generation effectively.

The next step is to identify the likely cause, apply a suitable improvement, and retest the original case and other related scenarios.

## 15. 📚 What I Learned

Through TECHFIX, I explored how to build a knowledge-based AI assistant using Dify.

Key learning outcomes include:

- 📂 Organizing technical knowledge for AI applications.
- ✂️ Understanding document processing and chunking.
- 🔎 Connecting knowledge retrieval with answer generation.
- 🧠 Understanding the basic RAG workflow.
- 📝 Applying prompt engineering to define assistant behavior.
- 🧪 Evaluating retrieval and answer quality separately.
- 🔍 Analyzing AI failures and identifying possible causes.
- 🛡️ Designing for safety, uncertainty, and knowledge limitations.
- 🔄 Improving an AI workflow through testing and iteration.

## 16. 🚀 Future Improvements

- 📚 Expand the knowledge base with additional reliable technical sources.
- ✂️ Improve document structure and chunking.
- 🔎 Review retrieval settings and relevance.
- 📝 Improve answer completeness without adding unsupported information.
- 🧪 Build a structured test dataset with expected results.
- 📊 Document test outcomes and compare results after changes.
- ❓ Improve the handling of incomplete and out-of-scope questions.
- 🛡️ Add more safety-related test scenarios.

## 17. 🔗 Project Links

- 🤖 **Dify Application:** https://udify.app/chat/rt8IYn25zm7BBkt8

## 18. 👩‍💻 Author

**Baraa Abu Watfa**

 AI & Automation*

---

🖥️ **TECHFIX — Turning Technical Knowledge into Practical Guidance.**
