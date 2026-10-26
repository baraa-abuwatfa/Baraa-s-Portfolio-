# U4 — GROUND ITS KNOWLEDGE

## Knowledge Engineering & RAG Systems

> Before trusting the answer, ground it in reliable knowledge.

في هذه الوحدة، أتعلم كيف أبني نظام ذكاء اصطناعي يعتمد على مصادر معرفة حقيقية، ويسترجع المعلومات المناسبة للإجابة عن أسئلة المستخدمين بدقة وموثوقية.

الهدف ليس مجرد إضافة ملفات إلى AI Assistant، بل فهم كيفية تجهيز المعرفة، وتحسين استرجاع المعلومات، وربط الإجابات بالأدلة، واختبار النظام وتحسين أدائه.

---

## 🎯 Capability

**Knowledge Engineering & RAG Systems**

القدرة على تصميم أنظمة ذكاء اصطناعي تعتمد على المعرفة، وتجهيز مصادر المعلومات، وهندسة عملية الاسترجاع، وتقييم جودة الإجابات ومدى استنادها إلى الأدلة.

---

## 🧠 What I Learned

خلال هذه الوحدة، طوّرت قدرتي على:

- **Define the Assistant:** تحديد هدف المساعد الذكي ونطاق عمله وتعليماته وقيود استخدامه.
- **Engineer the Knowledge:** تجهيز مصادر المعرفة وتنظيم المستندات ومعالجة النصوص وتقسيمها إلى أجزاء مناسبة.
- **Understand Embeddings & Search:** فهم التمثيلات الرقمية للنصوص والبحث الدلالي واسترجاع المعلومات.
- **Build RAG Workflows:** فهم كيفية الجمع بين استرجاع المعلومات وتوليد الإجابات باستخدام RAG.
- **Improve Retrieval Quality:** تحسين نتائج البحث باستخدام Chunking وTop-K وHybrid Search وReranking.
- **Ground AI Responses:** ربط الإجابات بالأدلة المسترجعة والاستشهاد بالمصادر عند الإمكان.
- **Evaluate AI Systems:** اختبار دقة الإجابات ومدى ارتباطها بالمصادر واكتشاف المعلومات غير المدعومة.
- **Handle Missing Knowledge:** تصميم سلوك مناسب عندما تكون المعلومات غير متوفرة أو غير كافية.
- **Improve System Performance:** تحليل الأخطاء وإجراء تجارب مضبوطة وتحسين النظام مع الحفاظ على جودة النتائج.


## 🔍 Engineering Focus

في هذه الوحدة، أركز على الأسئلة التالية:

1. ما الهدف من المساعد الذكي، وما حدود معرفته؟
2. كيف نختار مصادر معرفة موثوقة ومناسبة؟
3. كيف نعالج المستندات ونقسمها دون فقدان السياق؟
4. كيف يسترجع النظام المعلومات المرتبطة بسؤال المستخدم؟
5. كيف نختار حجم الأجزاء وعدد النتائج وطريقة البحث المناسبة؟
6. كيف نضمن أن الإجابة مدعومة بالأدلة المسترجعة؟
7. ماذا يحدث عندما تكون المعلومات ناقصة أو غير موجودة؟
8. كيف نميّز بين خطأ الاسترجاع وخطأ توليد الإجابة؟
9. كيف نختبر النظام ونقيس أداءه قبل إجراء التحسينات وبعدها؟

---

## 📌 Key Takeaway

**Understand the Knowledge. Engineer the Retrieval. Ground the Answer. Evaluate the System.**

افهم المعرفة، وهندس عملية الاسترجاع، واربط الإجابة بالأدلة، ثم اختبر النظام وحسّنه.
## 🛠️ Projects

### 01 — Guided Project

**Project:** TECHFIX — AI Computer Troubleshooting Assistant

An Arabic AI assistant that helps users understand common computer problems and find clear, safe troubleshooting guidance based on a specialized knowledge base.

- **Problem:** Users may struggle to understand computer problems and find reliable technical instructions in Arabic. General AI answers may also include unsupported information.
- **Solution:** Built an AI assistant that uses a specialized knowledge base to retrieve relevant technical information, provide initial troubleshooting guidance, request additional details when needed, and acknowledge when the available knowledge is insufficient.
- **Tools:** Dify, Knowledge Base, Retrieval-Augmented Generation (RAG), Large Language Model (LLM).

[Explore the Project](./05-control-its-agency/course-project)

### 02 — Independent Project

**Project:** QA Knowledge Assistant — Knowledge-Based Software Testing Assistant

An AI-powered assistant that helps users understand software testing concepts, classify reported issues, and prepare structured QA documentation using trusted reference materials.

- **Problem:** Beginner QA engineers and software testing students may struggle to apply testing concepts consistently, prepare test cases, and distinguish bugs from feature requests or improvements. General AI assistants may also generate unsupported answers when evidence is missing.
- **Solution:** Designed a knowledge-based assistant that uses RAG to retrieve information from QA reference documents and provide evidence-based guidance for software testing, issue classification, and QA documentation.
- **Tools:** Dify, Knowledge Base, Retrieval-Augmented Generation (RAG), Large Language Model (LLM).

[Explore the Project](./05-control-its-agency/independent-project)
---

## 📈 Capability Progress

- [ ] فهم دور قاعدة المعرفة في بناء AI Assistant.
- [ ] تحديد تعليمات المساعد ونطاق عمله وقيوده.
- [ ] تجهيز مصادر المعرفة ومعالجة المستندات.
- [ ] فهم Chunking وChunk Overlap وMetadata.
- [ ] فهم Embeddings وVector Search وHybrid Search.
- [ ] فهم RAG وربط الإجابات بالمعلومات المسترجعة.
- [ ] تحسين جودة الاسترجاع باستخدام Top-K وThreshold وReranking.
- [ ] تقييم Correctness وGroundedness واكتشاف Hallucinations.
- [ ] التعامل مع نقص المعرفة والامتناع عن الإجابة عند غياب الأدلة الكافية.
- [ ] اختبار النظام وتوثيق الأخطاء والتحسينات وإجراء Regression Testing.

---

## 🔗 Related Projects

- [Guided Project](https://github.com/baraa-abuwatfa/Baraa-s-Portfolio-/tree/7e926b3b9853431ae149e617f2ec8fb3f9a45ced/04-Grounding%20Thinking/course%20project)
- [Independent Project]([./independent-project](https://github.com/baraa-abuwatfa/Baraa-s-Portfolio-/tree/7e926b3b9853431ae149e617f2ec8fb3f9a45ced/04-Grounding%20Thinking/Independent%20Project))

---
