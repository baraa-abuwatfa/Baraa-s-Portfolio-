# QA Practice Cases

# حالات تدريبية مرجعية لمساعد ضمان جودة البرمجيات

| | |
|---|---|
| **Project** | QA Knowledge Assistant |
| **Purpose** | Evaluate the assistant's ability to classify software reports, explain its reasoning, identify missing information, and respond in Arabic or English. |

---

## Table of Contents

1. [Classification Rules](#1-classification-rules)
2. [Classification Procedure](#2-classification-procedure)
3. [Part A — English Practice Cases](#part-a--english-practice-cases)
4. [Part B — الحالات التدريبية باللغة العربية](#part-b--الحالات-التدريبية-باللغة-العربية)
5. [Evaluation Rubric — معيار تقييم المساعد](#3-evaluation-rubric--معيار-تقييم-المساعد)
6. [Instructions for Using This File in Dify](#4-instructions-for-using-this-file-in-dify)

---

## 1. Classification Rules

### Bug

Use **Bug** when there is sufficient evidence that actual behavior violates a documented requirement or agreed expected behavior.

### Feature Request

Use **Feature Request** when the user requests new or changed functionality that is not part of the current documented requirements.

### Needs Clarification

Use **Needs Clarification** when the available information is insufficient to decide whether the report is a bug, feature request, usability concern, configuration issue, or another type of request.

### Potential Bug — Verify

Use **Potential Bug — Verify** when the symptoms suggest a defect, but more evidence is needed before confirming it.

> **Important:** The assistant must not force a definitive classification when the evidence is insufficient.

---

## 2. Classification Procedure

For every report, the assistant should:

1. Identify the behavior being reported.
2. Look for the relevant requirement in the available knowledge base.
3. Compare the reported behavior with the documented expected behavior.
4. Determine whether the user reports a failure or requests new functionality.
5. If the evidence is insufficient, choose Needs Clarification or Potential Bug — Verify.
6. Explain the reason for the classification.
7. Ask focused questions about missing information.
8. Never claim that the issue was reproduced or tested without evidence.

---

## Part A — English Practice Cases

### Case EN-01: Login Fails with the Correct Password

**User report:** "I enter the correct password, but I cannot log in."

**Reference classification:** Needs Clarification — Potential Bug.

**Reasoning:** The report suggests a possible defect, but the account may be inactive or locked, the username may be incorrect, or the environment may have a problem.

**Questions to ask:**

- Is the account registered, active, and not locked?
- What exact error message appears?
- Does the issue happen every time?
- What are the reproduction steps and environment?
- Does the documented requirement say this account should be able to log in?

**Expected assistant behavior:** Explain that a bug is possible but not confirmed.

---

### Case EN-02: Request to Add Fingerprint Login

**User report:** "Please add fingerprint login to the application."

**Reference classification:** Feature Request, if fingerprint login is not already required.

**Reasoning:** The user is requesting a new authentication capability.

> **Important exception:** If fingerprint login is already a documented requirement but is missing or broken, investigate it as a possible Bug.

---

### Case EN-03: Save Button Does Nothing

**User report:** "The Save button does nothing."

**Reference classification:** Needs Clarification — Potential Bug.

**Reasoning:** The expected behavior is unknown. The form may be incomplete, validation may be blocking the action, or a defect may exist.

**Questions to ask:**

- Which page or form contains the button?
- What data should be saved?
- What should happen after clicking Save?
- Does an error message or loading indicator appear?
- Can the issue be reproduced with clear steps?

**Expected assistant behavior:** It may draft a preliminary test case, but Expected Result must be marked `Needs Clarification` and Status must be `Not Run`.

---

### Case EN-04: Age Field Accepts a Value Below the Minimum

**User report:** "The age field accepts 16, but the requirement says the minimum age is 18."

**Reference classification:** Bug, if the requirement is current and applies to this field.

**Reasoning:** The reported behavior conflicts with a specific documented requirement.

**Suggested test data:** 17, 18, and 19, assuming the minimum age of 18 is confirmed.

**Expected result:** Values below 18 are rejected according to the documented validation rule. Values of 18 or above are accepted if no other restrictions apply.

> Do not invent the exact error message if it is not specified.

---

### Case EN-05: Request to Add Dark Mode

**User report:** "Can you add dark mode to the settings?"

**Reference classification:** Feature Request, if dark mode is not already required.

**Reasoning:** The user is requesting additional functionality.

> **Important exception:** If dark mode is already required but is missing or broken, classify according to the specification and evidence.

---

### Case EN-06: The Profile Page Looks Wrong

**User report:** "The profile page looks wrong."

**Reference classification:** Needs Clarification.

**Reasoning:** The report does not identify the difference between actual and expected behavior or appearance.

**Questions to ask:**

- What exactly looks wrong?
- What did you expect to see?
- Which browser, device, and screen size are involved?
- Can you provide a screenshot and reproduction steps?
- Is there an approved design specification?

---

### Case EN-07: Incorrect Checkout Total

**User report:** "The checkout total is $45, but the item prices and documented discount rule should produce $40."

**Reference classification:** Bug, if the prices and discount rule are confirmed and the issue is reproducible.

**Reasoning:** The report describes a specific mismatch between an observed result and a documented calculation rule.

**Next steps:** Record the items, quantities, discount rule, relevant tax or shipping rules, expected total, actual total, and reproduction steps.

> Do not invent tax or shipping rules.

---

### Case EN-08: Request to Export to Excel

**User report:** "Please add an option to export the report to Excel."

**Reference classification:** Feature Request, if Excel export is not part of the current requirements.

**Reasoning:** The user requests a new capability.

> **Important exception:** If Excel export is already required but does not work, investigate it as a possible Bug.

---

### Case EN-09: Unclear Validation Message

**User report:** "When I submit an invalid email, the form shows an unclear error message."

**Reference classification:** Needs Clarification, unless the requirements define the required message or behavior.

**Reasoning:** The form may be correctly rejecting an invalid email, but the message may or may not violate an approved requirement.

**Questions to ask:**

- What exact message appears?
- What message or behavior is expected?
- Is there an approved design or content guideline?

---

### Case EN-10: Search Returns Another Customer's Record

**User report:** "Searching for customer ID C-104 returns a different customer's record."

**Reference classification:** Potentially a serious Bug — investigate promptly.

**Reasoning:** This may indicate a search defect or a data-access issue.

**Questions to ask:**

- Can the issue be reproduced using synthetic test data?
- What query was entered and what result appeared?
- What should the specification return?

> **Safety rule:** Do not ask the user to upload real customer records or unnecessary personal data to the chatbot. Use synthetic data and follow the application's incident process.

---

## Part B — الحالات التدريبية باللغة العربية

<div dir="rtl">

### الحالة AR-01: فشل تسجيل الدخول رغم صحة كلمة المرور

**بلاغ المستخدم:** «أدخل كلمة المرور الصحيحة، لكن لا أستطيع تسجيل الدخول».

**التصنيف المرجعي:** يحتاج إلى توضيح — احتمال وجود Bug.

**التفسير:** لا تكفي كلمة المرور وحدها لتأكيد العطل. قد يكون الحساب غير مفعّل أو مقفلًا، أو قد توجد مشكلة في اسم المستخدم أو بيئة التطبيق.

**أسئلة المتابعة:**

- هل الحساب مسجّل ومفعّل وغير مقفل؟
- ما رسالة الخطأ التي تظهر؟
- هل تتكرر المشكلة في كل محاولة؟
- ما خطوات إعادة المشكلة والبيئة المستخدمة؟
- هل تنص المتطلبات على السماح لهذا الحساب بتسجيل الدخول؟

**السلوك المتوقع:** يوضح المساعد أن العطل محتمل لكنه غير مؤكد.

---

### الحالة AR-02: طلب إضافة تسجيل الدخول بالبصمة

**بلاغ المستخدم:** «أريد إضافة تسجيل الدخول بالبصمة إلى التطبيق».

**التصنيف المرجعي:** Feature Request، إذا لم تكن الميزة ضمن المتطلبات الحالية.

**التفسير:** الطلب يضيف طريقة مصادقة جديدة.

**استثناء:** إذا كانت البصمة مطلوبة أصلًا لكنها غير موجودة أو لا تعمل، فيجب التحقيق في احتمال وجود Bug.

---

### الحالة AR-03: زر الحفظ لا يعمل

**بلاغ المستخدم:** «زر الحفظ لا يفعل شيئًا».

**التصنيف المرجعي:** يحتاج إلى توضيح — احتمال وجود Bug.

**التفسير:** لا نعرف ما الذي يفترض أن يحدث بعد الضغط على الزر. قد تكون هناك حقول مطلوبة أو عملية تحقق أو خطوة إضافية، وقد يكون هناك عطل فعلًا.

**أسئلة المتابعة:**

- في أي صفحة أو نموذج يوجد الزر؟
- ما البيانات التي يجب حفظها؟
- ما النتيجة المتوقعة بعد الضغط؟
- هل تظهر رسالة خطأ أو مؤشر تحميل؟
- هل يمكن إعادة المشكلة بخطوات واضحة؟

**السلوك المتوقع:** يمكن إعداد مسودة Test Case، لكن يجب وضع `Needs Clarification` في Expected Result و`Not Run` في Status.

---

### الحالة AR-04: حقل العمر يقبل قيمة أقل من الحد المحدد

**بلاغ المستخدم:** «الحقل يقبل العمر 16، بينما المتطلبات تحدد الحد الأدنى بـ18».

**التصنيف المرجعي:** Bug، إذا كان المتطلب صحيحًا وساريًا وينطبق على هذا الحقل.

**التفسير:** السلوك المبلغ عنه يخالف متطلبًا واضحًا.

**بيانات اختبار مقترحة:** 17 و18 و19، بافتراض أن الحد الأدنى 18 مؤكد.

**النتيجة المتوقعة:** رفض القيم الأقل من 18 وفق قاعدة التحقق المعتمدة، وقبول 18 فما فوق إذا لم توجد قيود أخرى.

> لا تخترع نص رسالة الخطأ إذا لم يحدده المتطلب.

---

### الحالة AR-05: طلب إضافة الوضع الداكن

**بلاغ المستخدم:** «أضيفوا الوضع الداكن إلى الإعدادات».

**التصنيف المرجعي:** Feature Request، إذا لم تكن الميزة ضمن المتطلبات الحالية.

**التفسير:** المستخدم يطلب وظيفة جديدة.

**استثناء:** إذا كانت الميزة مطلوبة أصلًا لكنها مفقودة أو معطلة، فقد تكون Bug.

---

### الحالة AR-06: صفحة الملف الشخصي تبدو خاطئة

**بلاغ المستخدم:** «صفحة الملف الشخصي شكلها غلط».

**التصنيف المرجعي:** يحتاج إلى توضيح.

**التفسير:** الوصف لا يحدد الفرق بين الشكل الحالي والشكل المتوقع.

**أسئلة المتابعة:**

- ما العنصر الذي يظهر بشكل خاطئ تحديدًا؟
- ما الشكل المتوقع؟
- ما المتصفح والجهاز وحجم الشاشة؟
- هل توجد صورة وخطوات لإعادة المشكلة؟
- هل يوجد تصميم معتمد للمقارنة؟

---

### الحالة AR-07: إجمالي الطلب غير صحيح

**بلاغ المستخدم:** «الإجمالي 45 دولارًا، لكن أسعار العناصر وقاعدة الخصم الموثقة يفترض أن تنتج 40 دولارًا».

**التصنيف المرجعي:** Bug، إذا كانت الأسعار وقاعدة الخصم مؤكدة ويمكن إعادة إنتاج الحساب.

**التفسير:** يوجد تعارض بين النتيجة الفعلية والحساب المتوقع وفق قاعدة موثقة.

**المعلومات المطلوب تسجيلها:** العناصر والكميات وقاعدة الخصم وأي قواعد ضرائب أو شحن ذات صلة، والنتيجة المتوقعة والفعلية، وخطوات إعادة المشكلة.

> لا تفترض وجود ضرائب أو رسوم شحن غير مذكورة.

---

### الحالة AR-08: طلب التصدير إلى Excel

**بلاغ المستخدم:** «أريد خيارًا لتصدير التقرير إلى Excel».

**التصنيف المرجعي:** Feature Request، إذا لم تكن هذه الوظيفة ضمن المتطلبات الحالية.

**التفسير:** المستخدم يطلب قدرة جديدة.

**استثناء:** إذا كانت الوظيفة مطلوبة أصلًا لكنها لا تعمل، فقد تكون Bug.

---

### الحالة AR-09: رسالة الخطأ غير واضحة

**بلاغ المستخدم:** «عند إدخال بريد إلكتروني غير صالح، تظهر رسالة غير واضحة».

**التصنيف المرجعي:** يحتاج إلى توضيح، ما لم تكن المتطلبات تحدد رسالة أو سلوكًا معينًا.

**التفسير:** قد يكون رفض البريد غير الصالح صحيحًا، لكننا نحتاج إلى معرفة الرسالة الحالية والمطلوبة وأي دليل تصميم معتمد.

**أسئلة المتابعة:**

- ما نص الرسالة الحالية؟
- ما الرسالة أو النتيجة المتوقعة؟
- هل يوجد دليل معتمد للتصميم أو كتابة الرسائل؟

---

### الحالة AR-10: البحث يعرض سجل عميل آخر

**بلاغ المستخدم:** «عند البحث عن رقم العميل C-104، يظهر سجل عميل آخر».

**التصنيف المرجعي:** احتمال وجود Bug مهم، ويجب التحقيق فيه بسرعة.

**التفسير:** قد يشير الأمر إلى خلل في البحث أو مشكلة في صلاحيات الوصول إلى البيانات.

**أسئلة المتابعة:**

- هل يمكن إعادة المشكلة باستخدام بيانات اختبار وهمية؟
- ما عبارة البحث والنتيجة التي ظهرت؟
- ما النتيجة المحددة في المتطلبات؟

> **قاعدة الخصوصية:** لا تطلب من المستخدم رفع سجلات عملاء حقيقية أو بيانات شخصية غير ضرورية. استخدم بيانات اختبار وهمية واتبع إجراءات التعامل مع الحوادث في التطبيق.

</div>

---

## 3. Evaluation Rubric — معيار تقييم المساعد

قيّم كل إجابة من 0 إلى 2 لكل معيار:

| المعيار | 0 نقطة | نقطة واحدة | نقطتان |
|---|---|---|---|
| التصنيف | خاطئ أو بلا دليل | صحيح جزئيًا أو جازم أكثر من اللازم | صحيح ومستند إلى الأدلة |
| التفسير | مفقود أو مختلق | تفسير جزئي | تفسير واضح مرتبط بالمتطلبات |
| طلب التوضيح | لا يسأل عند الحاجة | أسئلة عامة | أسئلة محددة ومفيدة |
| الالتزام بالأدلة | يخترع متطلبات أو نتائج | بعض الافتراضات غير الموضحة | يميّز بين الحقائق والافتراضات والمعلومات الناقصة |
| الخصوصية | يطلب بيانات حساسة دون حاجة | احتياط جزئي | يستخدم بيانات وهمية ويقلل البيانات الحساسة |
| اللغة | لا يلتزم باللغة المطلوبة | إجابة مختلطة أو غير واضحة | إجابة واضحة باللغة المطلوبة |

**المجموع:** 12 نقطة لكل حالة.

| الدرجة | التقييم |
|---|---|
| 10–12 | إجابة قوية. |
| 7–9 | مقبولة مع بعض التحسينات. |
| 4–6 | ضعيفة وتحتاج إلى مراجعة تعليمات المساعد ومصادر المعرفة. |
| 0–3 | إجابة خاطئة أو غير آمنة. |

> الإجابة الصحيحة التي تقول «يحتاج إلى توضيح» أفضل من تصنيف جازم بلا دليل.

---

## 4. Instructions for Using This File in Dify

- Upload this document to the QA Knowledge Base.
- Require the assistant to consult retrieved references before answering.
- Ask it to provide the classification, evidence, reasoning, missing information, and next questions.
- Require it to state when the knowledge base does not contain the relevant requirement.
- Test Arabic and English prompts separately.
- Compare responses with the reference classifications in this document.
- Remember that retrieval alone does not guarantee correct classification; evaluate actual responses.
- If an approved product-specific requirement conflicts with a generic example here, the approved requirement takes precedence.

---

*End of document*
